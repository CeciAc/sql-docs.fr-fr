---
title: Ensemble de lignes DISCOVER_CSDL_METADATA | Documents Microsoft
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
ms.assetid: a2d3cffd-a2c4-411c-b244-9e41ebe30939
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3bac193969cb4f5392944a79351b44390b013596
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051603"
---
# <a name="discovercsdlmetadata-rowset"></a>Ensemble de lignes DISCOVER_CSDL_METADATA
  Retourne des informations sur un modèle de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (tabulaire ou multidimensionnel), qui fournit la définition du modèle au format CSDLBI (Conceptual Schema Definition avec annotations BI). CSDLBI repose sur CSDL, un schéma XML exploité par l'infrastructure Entity Data Framework utilisée pour la communication entre un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et le client [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] . Les annotations Business Intelligence (BI) fournissent des métadonnées supplémentaires sur les modèles tabulaires et les objets qu'ils contiennent. Pour plus d’informations sur les modèles de données tabulaires, consultez [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](../../tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md).  
  
 Le contexte de sécurité de la commande affecte l'ensemble de lignes retourné. Les autorisations de lecture sur l'instance Analysis Services sont requises pour obtenir la définition CSDL à partir du serveur.  
  
 L'identificateur de langue du client qui émet la demande d'ensemble de lignes est inclus dans la chaîne de connexion pour la commande et affecte la langue affichée dans plusieurs propriétés retournées dans le cadre de l'ensemble de lignes.  Pour plus d'informations sur les propriétés et la description affectées par l'identificateur de langue, consultez la section Remarques.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_CSDL_METADATA` ensemble de lignes contient les colonnes suivantes.  
  
|**Nom de colonne**|**Indicateur de type**|**Restriction**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Oui|Spécifie le nom de la base de données pour laquelle la description CSDLBI est demandée. Si omis, le nom de la base de données active est utilisé.<br /><br /> Cette restriction est nécessaire pour tous les types de modèle.|  
|`PERSPECTIVE_ID`|`DBTYPE_WSTR`|Oui|Spécifie l'ID d'une perspective définie sur le modèle spécifié par CATALOG_NAME.<br /><br /> Restriction facultative. S'applique à tous les types de modèle.|  
|`PERSPECTIVE_NAME`|`DBTYPE_WSTR`|Oui|Spécifie le nom d'une perspective définie sur le modèle spécifié par CATALOG_NAME.<br /><br /> Cette restriction est nécessaire lorsque le modèle tabulaire inclut des perspectives ou lorsqu'une solution multidimensionnelle inclut plusieurs cubes ou perspectives.|  
|`METADATA`|`DBTYPE_WSTR`|non|Chaîne qui contient la définition XML d'une source de données et ses propriétés, d'après le schéma CSDLBI.|  
|`CUBE_ID`|`DBTYPE_WSTR`|Oui|Identificateur de chaîne.<br /><br /> Cette restriction est facultative pour les bases de données multidimensionnelles. Si plusieurs cubes sont disponibles et la restriction est omise, le cube par défaut est retourné.|  
  
## <a name="remarks"></a>Notes  
 DISCOVER_CSDL_METADATA a les configurations requises suivantes :  
  
-   La demande DISCOVER échouera si un base de données n'est pas spécifiée en utilisant la restriction CATALOG_NAME.  
  
-   Pour un modèle tabulaire, un ID de perspective est nécessaire s'il existe plusieurs perspectives dans le modèle.  
  
-   Pour les modèles multidimensionnels, le nom de catalogue et le nom de cube (perspective) sont obligatoires.  
  
-   Si une perspective est fournie comme restriction, le même ensemble de lignes CSDL est retourné pour le modèle. Toutefois, tous les objets présents dans le modèle, mais qui ne sont pas inclus dans la perspective spécifiée sont marqués comme `Hidden` = True.  
  
-   Pour les tables et les colonnes, la demande DISCOVER retourne toujours une valeur de la dimension du cube. Si la propriété de dimension du cube n'est pas définie, la demande retourne la valeur de la dimension.  
  
-   La demande DISCOVER ne peut pas retourner toutes les mesure ou les colonnes calculées qui contiennent une erreur sémantique.  
  
-   La demande DISCOVER ne retournera pas d'informations pour les objets qui n'ont pas de valeurs de propriété. De même, la demande DISCOVER ne retournera pas de valeurs pour les attributs qui utilisent la valeur par défaut.  
  
 La chaîne XML retournée dans l'ensemble de lignes peut inclure les propriétés ou valeurs spécifiques à une langue qui suivent. Par exemple, si vous émettez la demande d'ensemble de lignes à partir d'un client qui dont le LCID est 0403 (Catalan), la propriété retournera les valeurs approprié au catalan suivantes. Si les traductions ne sont pas disponibles sur le serveur, la chaîne de la langue par défaut du serveur est retournée.  
  
-   Légende  
  
-   Qualificateur  
  
-   SortDirection  
  
-   IsRightToLeft  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 La requête XMLA suivante retourne la représentation CSDL de l'exemple de modèle tabulaire AdventureWorks 2012. Chaque solution tabulaire ne peut contenir qu'un seul modèle, la restriction PERSPECTIVE_NAME peut donc rester vide. Toutefois, ce modèle contient plusieurs perspectives.  
  
```  
  
<Discover  xmlns="urn:schemas-microsoft-com:xml-analysis">  
     <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
                <CATALOG_NAME>AdventureWorks2012Tabular</CATALOG_NAME>  
                <PERSPECTIVE_NAME>EMPLOYEE</PERSPECTIVE_NAME>  
                <VERSION>2.0</VERSION>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
                <PropertyList>  
                </PropertyList>  
         </Properties>  
</Discover>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 La requête XMLA suivante retourne les représentations CSDLBI du cube Contoso Operations. La restriction VERSION est requise pour exécuter une requête sur une base de données multidimensionnelle. La base de données Contoso Retail contient deux cubes. Par conséquent, le cube Operations est référencé à l'aide de la restriction PERSPECTIVE_NAME.  
  
```  
  
<Discover  xmlns="urn:schemas-microsoft-com:xml-analysis">  
     <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
                <CATALOG_NAME>Contoso_Retail</CATALOG_NAME>  
                <PERSPECTIVE_NAME>Operation</PERSPECTIVE_NAME>  
                <VERSION>2.0</VERSION>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
                <PropertyList>  
                </PropertyList>  
         </Properties>  
 </Discover>  
  
```  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|3444B255-171E-4cb9-AD98-19E57888A75F|  
|ADOMDNAME|Csdl|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma de Analysis Services](../analysis-services-schema-rowsets.md)   
 [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](../../tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
  