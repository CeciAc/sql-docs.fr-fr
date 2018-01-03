---
title: "Prise en charge des colonnes éparses (ODBC) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d872db9430c2d7b85f4d6e685a3e3f2550eb8015
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sparse-columns-support-odbc"></a>Prise en charge des colonnes éparses (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Cette rubrique décrit la prise en charge ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour les colonnes éparses. Pour un exemple illustrant la prise en charge ODBC pour les colonnes éparses, consultez [appeler le SQLColumns sur une Table avec des colonnes éparses](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Pour plus d’informations sur les colonnes éparses, consultez [Sparse Columns Support in SQL Server Native Client](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Métadonnées d'instruction  
 Le champ de descripteur APD (Application Parameter Descriptor) et l'attribut d'instruction SQL_SOPT_SS_NAME_SCOPE acceptent les valeurs supplémentaires SQL_SS_NAME_SCOPE_EXTENDED et SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Ces valeurs spécifient les colonnes à inclure dans le jeu de résultats retourné par [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md). Pour plus d’informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Un nouveau descripteur de ligne d'implémentation (IRD, Implementation Row Descriptor), un champ SQLSMALLINT en lecture seule appelé SQL_CA_SS_IS_COLUMN_SET, peut être utilisé pour déterminer si une colonne est une valeur **column_set** XML. SQL_CA_SS_IS_COLUMN_SET prend les valeurs SQL_TRUE et SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Métadonnées de catalogue  
 Deux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des colonnes spécifiques (SS_IS_SPARSE et SS_IS_COLUMN_SET) ont été ajoutés au jeu de résultats pour [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Prise en charge de fonction ODBC pour les colonnes éparses  
 Les fonctions ODBC suivantes ont été mises à jour pour prendre en charge les colonnes éparses dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  