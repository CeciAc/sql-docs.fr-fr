---
title: Sys.geo_replication_links (base de données Azure SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_links_TSQL
- dm_geo_replication_links
- sys.dm_geo_replication_links
- sys.dm_geo_replication_links_TSQL
helpviewer_keywords:
- sys.dm_geo_replication_links dynamic management view
- dm_geo_replication_links dynamic management view
ms.assetid: 58911798-1d60-4f28-87ab-2def2bfc3de7
author: mashamsft
ms.author: mathoma
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6e768f447cd53321861eae91bbe40e2e34ad12f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043164"
---
# <a name="sysgeoreplicationlinks-azure-sql-database"></a>sys.geo_replication_links (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque lien de réplication entre les bases de données primaires et secondaires dans un partenariat de géo-réplication. Cette vue se trouve dans la base de données master logique.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id|**Int**|ID de la base de données actuel dans la vue sys.databases.|  
|start_date|**datetimeoffset**|Heure UTC dans un centre de données SQL de base de données régionaux lors de la réplication de base de données a été initiée|  
|modify_date|**datetimeoffset**|Heure UTC à centre de données SQL de base de données régional lorsque la base de données géo-réplication est terminée. La nouvelle base de données est synchronisée avec la base de données primaire à compter de cette heure. .|  
|link_guid|**uniqueidentifier**|ID unique de la liaison de géo-réplication.|  
|partner_server|**sysname**|Nom du serveur de base de données SQL contenant la base de données de géo-répliquée.|  
|partner_database|**sysname**|Nom de la base de données géo-répliqué sur le serveur lié de la base de données SQL.|  
|replication_state|**tinyint**|L’état de géo-réplication pour cette base de données :.<br /><br /> 0 = en attente. La création de la base de données secondaire active est planifiée, mais les étapes de préparation nécessaires ne sont pas encore terminées.<br /><br /> 1 = Seeding. La cible de géo-réplication est en cours d’amorçage, mais les deux bases de données ne sont pas encore synchronisés. Jusqu'à ce que l’amorçage terminé, vous ne peut pas se connecter à la base de données secondaire. Suppression de base de données secondaire du site principal annulera l’opération d’amorçage.<br /><br /> 2 = mise à jour. La base de données secondaire est dans un état transactionnellement cohérent et est constamment synchronisé avec la base de données primaire.|  
|replication_state_desc|**nvarchar (256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|role|**tinyint**|Rôle de géo-réplication, une des :<br /><br /> 0 = primary. Le database_id fait référence à la base de données primaire dans le partenariat de géo-réplication.<br /><br /> 1 = la base de données secondaire.  Le database_id fait référence à la base de données primaire dans le partenariat de géo-réplication.|  
|role_desc|**nvarchar (256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Le type secondaire, un des suivants :<br /><br /> 0 = Non. La base de données secondaire n’est pas accessible jusqu’au basculement.<br /><br /> 1 = lecture seule. La base de données secondaire est accessible uniquement aux connexions clientes avec ApplicationIntent = ReadOnly.<br /><br /> 2 = Toutes. La base de données secondaire est accessible à toute connexion cliente.|  
|secondary_allow_connections _desc|**nvarchar (256)**|Non<br /><br /> Tous<br /><br /> En lecture seule|  
  
## <a name="permissions"></a>Autorisations

Cette vue est disponible uniquement dans le **master** base de données pour la connexion du principal au niveau du serveur.  
  
## <a name="example"></a>Exemple

Afficher toutes les bases de données avec des liens de géo-réplication.  

```sql
SELECT
     database_id  
   , start_date  
   , partner_server  
   , partner_database  
   , replication_state  
   , role_desc  
   , secondary_allow_connections_desc
FROM sys.geo_replication_links;  
```

## <a name="see-also"></a>Voir aussi

 [ALTER DATABASE (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys.dm_geo_replication_link_status &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [Sys.dm_operation_status &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
