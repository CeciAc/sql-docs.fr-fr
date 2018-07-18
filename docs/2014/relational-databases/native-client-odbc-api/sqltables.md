---
title: SQLTables | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d918f1c64350e3a43976e2e13d1dd02f21620e6a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420978"
---
# <a name="sqltables"></a>SQLTables
  SQLTables peut être exécutée sur un curseur côté serveur statique. Une tentative d’exécution SQLTables sur un curseur modifiable (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 SQLTables signale les tables de toutes les bases de données lorsque le *CatalogName* paramètre est SQL_ALL_CATALOGS et que tous les autres paramètres contiennent des valeurs par défaut (pointeurs NULL).  
  
 Pour signaler les catalogues disponibles, les schémas et les types de tables, SQLTables fait une utilisation particulière des chaînes vides (pointeurs d’octets de longueur nulle). Les chaînes vides ne sont pas des valeurs par défaut (pointeurs NULL).  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge des informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *nom_serveur_lié.Nom_Catalogue*.  
  
 SQLTables retourne d’informations sur les tables dont les noms correspondent à *TableName* et sont détenus par l’utilisateur actuel.  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables et paramètres table  
 Lorsque l’attribut d’instruction SQL_SOPT_SS_NAME_SCOPE a la valeur SQL_SS_NAME_SCOPE_TABLE_TYPE, plutôt que sa valeur par défaut SQL_SS_NAME_SCOPE_TABLE, SQLTables retourne des informations sur les types de table. La valeur TABLE_TYPE retournée pour un type de table dans la colonne 4 du jeu de résultats retourné par SQLTables est un TYPE de TABLE. Pour plus d’informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Les tables, les vues et les synonymes partagent un espace de noms commun, distinct de l'espace de noms utilisé par les types de table. Bien qu'il ne soit pas possible d'avoir une table et une vue ayant le même nom, vous pouvez avoir une table et un type de table avec le même nom dans le même catalogue et le même schéma.  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Exemple  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQLTables (fonction)](http://go.microsoft.com/fwlink/?LinkId=59374)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
