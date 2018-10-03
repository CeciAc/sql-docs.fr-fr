---
title: Sys.dm_db_column_store_row_group_operational_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31b71c68-50a0-4fd8-a7fe-2d2292be1163
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b4d3c98f54f6f72d111f96e58e1ddafaab27e949
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782817"
---
# <a name="sysdmdbcolumnstorerowgroupoperationalstats-transact-sql"></a>sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne actuel d’e/s, verrouillage, au niveau des lignes et méthode d’accès pour les rowgroups compressés dans un index columnstore. Utilisez **sys.dm_db_column_store_row_group_operational_stats** pour effectuer le suivi de la durée pendant laquelle une requête de l’utilisateur doit attendre pour lire ou écrire dans un rowgroup compressé ou une partition d’un index columnstore et identifier les rowgroups qui se produisent une activité d’e/s importante ou des zones réactives.  
  
 Les index columnstore en mémoire n’apparaissent pas dans cette vue DMV.  
 
 
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de la table contenant l’index columnstore.|  
|**index_id**|**Int**|ID de l'index columnstore.|  
|**partition_number**|**Int**|Numéro de partition (basé sur la valeur 1) au sein de l'index ou du segment de mémoire.|  
|**row_group_id**|**Int**|ID du rowgroup dans l’index columnstore. Il est unique au sein d’une partition.|  
|**scan_count**|**Int**|Nombre d’analyses via le groupe de lignes depuis le dernier redémarrage SQL.|  
|**delete_buffer_scan_count**|**Int**|Nombre de fois où que le tampon de suppression a été utilisé pour déterminer les lignes supprimées dans ce groupe de lignes. Cela inclut l’accès à la table de hachage en mémoire et de l’arbre b sous-jacent.|  
|**index_scan_count**|**Int**|Nombre de fois que la partition d’index columnstore a été analysée. Cela est identique pour tous les rowgroups dans la partition.|  
|**rowgroup_lock_count**|**bigint**|Nombre cumulatif de demandes de verrous pour ce groupe de lignes depuis le dernier redémarrage SQL.|  
|**rowgroup_lock_wait_count**|**bigint**|Nombre cumulatif de fois où le moteur de base de données a attendu sur ce verrou de groupe de lignes depuis le dernier redémarrage SQL.|  
|**rowgroup_lock_wait_in_ms**|**bigint**|Nombre cumulatif de millisecondes le moteur de base de données a attendu sur ce verrou de groupe de lignes depuis le dernier redémarrage SQL.|  
  
## <a name="permissions"></a>Permissions  
 Les autorisations suivantes sont nécessaires :  
  
-   Autorisation CONTROL sur la table spécifiée par object_id.  
  
-   Autorisation VIEW DATABASE STATE pour retourner des informations sur tous les objets au sein de la base de données, à l’aide de l’objet générique @*object_id* = NULL  
  
 L'octroi de l'autorisation VIEW DATABASE STATE autorise le renvoi de tous les objets de la base de données, quelles que soient les autorisations CONTROL refusées sur des objets spécifiques.  
  
 Le refus de l'autorisation VIEW DATABASE STATE interdit le retour de tous les objets de la base de données, quelles que soient les autorisations CONTROL accordées sur des objets spécifiques. Également, lorsque le caractère de base de données générique @*database_id*= NULL est spécifiée, la base de données est omis.  
  
 Pour plus d’informations, consultez [fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux index &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)   
 [sys.dm_os_latch_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)   
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)   
 [Sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  

