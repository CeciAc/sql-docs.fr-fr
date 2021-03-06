---
title: sys.pdw_replicated_table_cache_state (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2ae652f584ceaad62379256f822527a316c30f89
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401736"
---
# <a name="syspdw_replicated_table_cache_state-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Retourne l’état du cache associé à une table répliquée par **object_id**.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**tiers**|ID d’objet de la table. Consultez [sys. objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** est la clé de cette vue.||  
|state|**nvarchar (40)**|État du cache de la table répliquée pour cette table.|« Nochapy », « Ready »|  
  
## <a name="example"></a>Exemple
Cet exemple joint sys. pdw_replicated_table_cache_state à sys. tables pour récupérer le nom de la table et l’état du cache de la table répliquée.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Étapes suivantes  
 Pour obtenir la liste de tous les affichages catalogue pour SQL Data Warehouse et les Data Warehouse parallèles, consultez [SQL Data Warehouse et les affichages catalogue de Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
