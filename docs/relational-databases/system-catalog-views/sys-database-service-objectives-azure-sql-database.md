---
title: "Sys.database_service_objectives (de base de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 08/30/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "Pool élastique"
- "pool élastique, gestion"
f1_keywords: DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: "16"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d1ccfea9f9c24312d29be192e5b6497c89e7972
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>Sys.database_service_objectives (de base de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retourne l’édition (niveau de service), l’objectif de service (niveau de tarification) et le nom du pool élastique, si elle existe, pour une base de données SQL Azure ou d’un entrepôt de données SQL Azure. Si vous ouvrez une session à la base de données master sur un serveur de base de données SQL Azure, retourne des informations sur toutes les bases de données. Pour l’entrepôt de données SQL Azure, vous devez être connecté à la base de données master.  
  
  
 Pour plus d’informations sur la tarification, consultez [les options de base de données SQL et les performances : tarification de base de données SQL](https://azure.microsoft.com/en-us/pricing/details/sql-database/) et [tarification de l’entrepôt de données SQL](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Pour modifier les paramètres de service, consultez [ALTER DATABASE (base de données de SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) et [ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 La vue sys.database_service_objectives contient les colonnes suivantes.  
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_id|int|ID de la base de données unique dans une instance du serveur de base de données SQL Azure. Joignable avec [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|édition|sysname|Le niveau de service pour l’entrepôt de données ou de la base de données : **base**, **Standard**, **Premium** ou **Data Warehouse**.|  
|service_objective|sysname|Le niveau de tarification de la base de données. Si la base de données est dans un pool élastique, retourne **ElasticPool**.<br /><br /> Sur le **base** au niveau, retourne **base**.<br /><br /> **Base de données dans un niveau de service standard** renvoie l’une des opérations suivantes : S0, S1, S2 ou S3.<br /><br /> **La base de données unique dans un niveau premium** retourne des éléments suivants : P1, P2, P4, P6/P3 ou P11.<br /><br /> **SQL Data Warehouse** retourne DW100 via DW2000.|  
|elastic_pool_name|sysname|Le nom de la [pool élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) appartenant à la base de données. Retourne **NULL** si la base de données est une base de données ou un warehoue de données.|  
  
## <a name="permissions"></a>Permissions  
 Requiert **dbManager** autorisation sur la base de données master.  Au niveau de la base de données, l’utilisateur doit être le créateur ou le propriétaire.  
  
## <a name="examples"></a>Exemples  
 Cet exemple peut être exécuté sur la base de données master ou sur les bases de données utilisateur. La requête retourne le nom, service et informations de niveau de performances des bases de données.  
  
```tsql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  