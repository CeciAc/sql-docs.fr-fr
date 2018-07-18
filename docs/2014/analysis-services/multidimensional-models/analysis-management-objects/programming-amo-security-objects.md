---
title: Programmation des objets de sécurité AMO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, security
- AMO, security
ms.assetid: 5d963721-6e6e-46eb-bc9b-18724dd0b751
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e110e71630a43d30f29be89cd56197ab8f18fd7b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197949"
---
# <a name="programming-amo-security-objects"></a>Programmation d'objets de sécurité AMO
  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], programmation des objets de sécurité ou l’exécution des applications qui utilisent des objets de sécurité AMO exige d’être membre du groupe administrateur du serveur ou le groupe administrateur de base de données. Administrateur du serveur et l’administrateur de base de données sont un accès niveaux fournie par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], l'accès utilisateur à tout objet est obtenu à travers la combinaison des rôles et des autorisations attribués à cet objet. Pour plus d’informations, consultez [Classes de sécurité AMO](amo-security-classes.md).  
  
## <a name="role-and-permission-objects"></a>Objets de rôle et d'autorisation  
 Les rôles de serveur contiennent un seul et même rôle dans la collection : le rôle Administrateurs. Il n'est pas possible d'ajouter de nouveaux rôles à la collection des rôles de serveur. L'appartenance au rôle Administrateurs autorise un accès complet à chaque objet du serveur  
  
 Les objets <xref:Microsoft.AnalysisServices.Role> sont créés au niveau de la base de données. La maintenance de rôle revient simplement à ajouter ou supprimer des membres au niveau du rôle et à ajouter ou supprimer des rôles dans l'objet <xref:Microsoft.AnalysisServices.Database>. Un rôle ne peut pas être supprimé si un objet <xref:Microsoft.AnalysisServices.Permission> lui est associé. Pour supprimer un rôle, tous les <xref:Microsoft.AnalysisServices.Permission> des objets dans le <xref:Microsoft.AnalysisServices.Database> objets doivent être recherchés et le <xref:Microsoft.AnalysisServices.Role> supprimé des autorisations, avant le <xref:Microsoft.AnalysisServices.Role> peuvent être supprimés de la <xref:Microsoft.AnalysisServices.Database>.  
  
 Les autorisations définissent les actions pouvant être effectuées sur les objets qui en bénéficient. Les autorisations peuvent être fournies aux objets suivants : <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MiningStructure> et <xref:Microsoft.AnalysisServices.MiningModel>. La maintenance des autorisations implique d'octroyer ou de révoquer l'accès par la propriété d'accès correspondante. À chaque accès autorisé correspond une propriété qui peut être définie selon le niveau d'accès souhaité. L'accès peut être défini pour les opérations suivantes : Process, ReadDefinition, Read, Write et Administer. L'accès Administer n'est défini qu'au niveau de l'objet <xref:Microsoft.AnalysisServices.Database>. Le niveau de sécurité de l'administrateur de base de données est obtenu lorsque le rôle est accordé avec l'autorisation de base de données Administer.  
  
 L'exemple suivant crée quatre rôles : Database Administrators (Administrateurs de base de données), Processors (Processeurs), Writers (Enregistreurs) et Readers (Lecteurs).  
  
 Les administrateurs de base de données peuvent gérer la base de données fournie.  
  
 Les processeurs peuvent traiter tous les objets d'une base de données et vérifier les résultats. Pour vérifier les résultats, l'accès en lecture à l'objet de base de données doit être explicitement activé sur le cube fourni, car l'autorisation de lecture ne s'applique pas aux objets enfants.  
  
 Les enregistreurs peuvent lire et enregistrer sur le cube fourni, tandis que l'accès aux cellules est limité aux États-Unis (« United States ») dans la dimension « Customer » (Client).  
  
 Les lecteurs peuvent lire sur le cube fourni, tandis que l'accès aux cellules est limité aux États-Unis (« United States ») dans la dimension « Customer » (Client).  
  
```  
static public void CreateRolesAndPermissions(Database db, Cube cube)  
{  
    Role role;  
    DatabasePermission dbperm;  
    CubePermission cubeperm;  
  
    #region Create the Database Administrators role  
  
    // Create the Database Administrators role.  
    role = db.Roles.Add("Database Administrators");  
    role.Members.Add(new RoleMember("")); // e.g. domain\user  
    role.Update();  
  
    // Assign administrative permissions to this role.  
    // Members of this role can perform any operation within the database.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Administer = true;  
    dbperm.Update();  
  
    #endregion  
  
    #region Create the Processors role  
  
    // Create the Processors role.  
    role = db.Roles.Add("Processors");  
    role.Members.Add(new RoleMember("")); // e.g. myDomain\johndoe  
    role.Update();  
  
    // Assign Read and Process permissions to this role.  
    // Members of this role can process objects in the database and query them to verify results.  
    // Process permission applies to all contained objects, i.e. all dimensions and cubes.  
    // Read permission does not apply to contained objects, so we must assign the permission explicitly on the cubes.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Process = true;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Writers role  
  
    // Create the Writers role.  
    role = db.Roles.Add("Writers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read and Write permissions to this role.  
    // Members of this role can discover, query and writeback to the Adventure Works cube.  
    // However cell access and writeback is restricted to the United States (in the Customer dimension).  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Write = WriteAccess.Allowed;  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.Read, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.ReadWrite, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Readers role  
  
    // Create the Readers role.  
    role = db.Roles.Add("Readers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read permissions to this role.  
    // Members of this role can discover and query the Adventure Works cube.  
    // However the Customer dimension is restricted to the United States.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    Dimension dim = db.Dimensions.GetByName("Customer");  
    DimensionAttribute attr = dim.Attributes.GetByName("Country-Region");  
    CubeDimensionPermission cubedimperm = cubeperm.DimensionPermissions.Add(dim.ID);  
    cubedimperm.Read = ReadAccess.Allowed;  
    AttributePermission attrperm = cubedimperm.AttributePermissions.Add(attr.ID);  
    attrperm.AllowedSet = "{[Customer].[Country-Region].[Country-Region].&[United States]}";  
    cubeperm.Update();  
  
    #endregion  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices>   
 [Présentation des Classes AMO](amo-classes-introduction.md)   
 [Programmation d’objets AMO sécurité](programming-amo-security-objects.md)   
 [Autorisations et droits d’accès &#40;Analysis Services - données multidimensionnelles&#41;](https://msdn.microsoft.com/library/ms174786(v=sql.120).aspx)   
 [Sécurisation de l’Instance Analysis Services](https://technet.microsoft.com/library/ms175663\(v=sql.110\).aspx)   
 [Architecture logique &#40;Analysis Services - données multidimensionnelles&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Objets de base de données &#40;Analysis Services - données multidimensionnelles&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
