---
title: Sys.dm_database_copies (base de données Azure SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d11f152d4d3d929baeab04cbf44e3a4b2848f456
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640467"
---
# <a name="sysdmdatabasecopies-azure-sql-database"></a>sys.dm_database_copies (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur une copie de base de données.  
  
Pour retourner des informations sur les liens de géo-réplication, utilisez le [sys.geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md) ou [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) vues (disponibles dans SQL Database V12).
  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**Int**|ID de la base de données active dans la vue `sys.databases`.|  
|**start_date**|**datetimeoffset**|Heure UTC dans un centre de données [!INCLUDE[ssSDS](../../includes/sssds-md.md)] local lorsque la copie de la base de données a été initialisée.|  
|**modify_date**|**datetimeoffset**|Heure UTC dans un centre de données [!INCLUDE[ssSDS](../../includes/sssds-md.md)] local lorsque la copie de la base de données s'est terminée. La nouvelle base de données est cohérente d'un point de vue transactionnel avec la base de données primaire à compter de ce moment. Les informations d’exécution sont mis à jour toutes les minutes.<br /><br />Heure UTC qui reflète la dernière mise à jour du champ percent_complete.|  
|**percent_complete**|**real**|Pourcentage des octets copiés. Les valeurs valides sont comprises entre 0 et 100. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] résout automatiquement certaines erreurs, telles qu'un basculement, et redémarre la copie de base de données. Dans ce cas, percent_complete redémarre à 0.|  
|**error_code**|**Int**|Lorsque la valeur est supérieure à 0, le code indique une erreur qui s'est produite lors de la copie. Si la valeur est égale à 0, aucune erreur ne s'est produite.|  
|**error_desc**|**nvarchar(4096)**|Description de l'erreur qui s'est produite lors de la copie.|  
|**error_severity**|**Int**|Retourne 16, si la copie de la base de données a échoué.|  
|**error_state**|**Int**|Retourne 1, si la copie a échoué.|  
|**copy_guid**|**uniqueidentifier**|ID unique de l’opération de copie.|  
|**partner_server**|**sysname**|Nom du serveur de base de données SQL dans laquelle la copie est créée.|  
|**partner_database**|**sysname**|Nom de la copie de base de données sur le serveur partenaire.|  
|**replication_state**|**tinyint**|L’état de réplication de copie continue pour cette base de données. Valeurs possibles :<br /><br /> 0 = en attente. La création de la copie de base de données est planifiée, mais les étapes de préparation nécessaires ne sont pas encore terminées ou sont temporairement bloquées par le quota d’amorçage.<br /><br /> 1 = Seeding. La base de données de copie en cours d’amorçage n'est pas encore entièrement synchronisée avec la base de données source. Dans cet état, vous ne peut pas se connecter à la copie. Pour annuler l’opération d’amorçage en cours d’exécution, la base de données de copie doit être supprimée.|  
|**replication_state_desc**|**nvarchar (256)**|Description de replication_state :<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**Int**|Champ réservé.|  
|**is_continuous_copy**|**bit**|0 = retourne 0|  
|**is_target_role**|**bit**|0 = la base de données source<br /><br /> 1 = la base de données de copie|  
|**is_interlink_connected**|bit|Champ réservé.|  
|**is_offline_secondary**|bit|Champ réservé.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue est disponible uniquement dans le **master** base de données pour la connexion du principal au niveau du serveur.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **sys.dm_database_copies** afficher dans le **master** base de données de la source ou la cible [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server. Lorsque la copie de base de données s’achève avec succès et la nouvelle base de données devient ONLINE, la ligne dans le **sys.dm_database_copies** vue est supprimée automatiquement.  
  
  
