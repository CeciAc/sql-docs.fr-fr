---
title: log_shipping_monitor_secondary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_secondary_TSQL
- log_shipping_monitor_secondary
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_secondary system table
ms.assetid: afbe1bb7-89a7-4020-9408-0af64a043c2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 838c810c28c03ae11237f449483789ed8dbbf740
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989960"
---
# <a name="logshippingmonitorsecondary-transact-sql"></a>log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke un enregistrement de surveillance par base de données secondaire dans une configuration de la copie des journaux de transaction. Cette table est stockée dans le **msdb** base de données.  
  
 Les tables liées à l'historique et à la surveillance sont également utilisées au niveau du serveur principal et des serveurs secondaires.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**secondary_server**|**sysname**|Le nom de l’instance secondaire de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans la configuration d’envoi de journaux.|  
|**secondary_database**|**sysname**|Nom de la base de données secondaire dans la configuration de la copie des journaux de transactions.|  
|**secondary_id**|**uniqueidentifier**|ID du serveur secondaire dans la configuration d'envoi de journaux.|  
|**primary_server**|**sysname**|Le nom de l’instance principale de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans la configuration d’envoi de journaux.|  
|**primary_database**|**sysname**|Nom de la base de données primaire dans la configuration d'envoi de journaux.|  
|**restore_threshold**|**int**|Nombre de minutes pouvant s'écouler entre les opérations de restauration avant qu'une alerte ne soit générée.|  
|**threshold_alert**|**Int**|L’alerte à déclencher lorsque le seuil de restauration est dépassé.|  
|**threshold_alert_enabled**|**bit**|Détermine si les alertes de seuil de restauration sont activées. 1 = Activé.<br /><br /> 0 = Désactivées.|  
|**last_copied_file**|**nvarchar(500)**|Nom de fichier du dernier fichier de sauvegarde copié sur le serveur secondaire.|  
|**last_copied_date**|**datetime**|Heure et date de la dernière copie sur le serveur secondaire.|  
|**last_copied_date_utc**|**datetime**|Date et heure de la dernière opération de copie sur le serveur secondaire, au format UTC (Coordinated Universal Time).|  
|**last_restored_file**|**nvarchar(500)**|Nom du dernier fichier de sauvegarde restauré dans la base de données secondaire.|  
|**last_restored_date**|**datetime**|Heure et date auxquelles a eu lieu la dernière opération de restauration de la base de données secondaire.|  
|**last_restored_date_utc**|**datetime**|Date et heure de la dernière opération de restauration sur la base de données secondaire, au format UTC (Coordinated Universal Time).|  
|**last_restored_latency**|**int**|Durée écoulée (en minutes) entre la création de la sauvegarde du journal sur le serveur principal et sa restauration sur le serveur secondaire.<br /><br /> La valeur initiale est NULL.|  
|**history_retention_period**|**int**|Durée de conservation (en minutes) des enregistrements historiques d'envoi des journaux pour une base de données secondaire donnée avant leur suppression.|  
  
## <a name="remarks"></a>Notes  
 Sont stockées sur le serveur moniteur distant, et les informations liées à un serveur secondaire sont également stockées sur le serveur secondaire dans son **log_shipping_monitor_secondary** table.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
