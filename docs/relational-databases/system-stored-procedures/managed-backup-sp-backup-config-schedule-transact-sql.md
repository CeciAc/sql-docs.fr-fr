---
title: managed_backup.sp_backup_config_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 52df69439cecad5fddf3d38b8852a1ce86cc4dbd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942071"
---
# <a name="managedbackupspbackupconfigschedule-transact-sql"></a>managed_backup.sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Configure les options de planification automatisées ou personnalisées pour [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
    
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'
    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="Arguments"></a> Arguments  
 @database_name  
 Le nom de la base de données, permettant la gestion de sauvegarde sur une base de données spécifique. Si NULL ou *, cette sauvegarde managée s’appliqu’à toutes les bases de données sur le serveur.  
  
 @scheduling_option  
 Spécifiez 'System' pour la planification de sauvegarde système contrôlé. Spécifiez 'Personnalisé' pour un calendrier personnalisé défini par les autres paramètres.  
  
 @full_backup_freq_type  
 Le type de fréquence pour l’opération de sauvegarde managé, qui peut être définie sur « Quotidien » ou « Hebdomadaires ».  
  
 @days_of_week  
 Les jours de la semaine pour les sauvegardes lorsque @full_backup_freq_type est définie sur toutes les semaines. Spécifiez les noms de chaîne complet comme « Lundi ».  Vous pouvez également spécifier plus que le nom d’une journée, séparé par une barre verticale. Par exemple N'Monday | Mercredi | Vendredi ».  
  
 @backup_begin_time  
 L’heure de début de la fenêtre de sauvegarde. Les sauvegardes ne démarrera pas en dehors de la fenêtre de temps, ce qui est définie par une combinaison de @backup_begin_time et @backup_duration.  
  
 @backup_duration  
 La durée de la fenêtre de temps de sauvegarde. Notez qu’il n’existe aucune garantie que les sauvegardes seront terminées au cours de la fenêtre de temps définie par @backup_begin_time et @backup_duration. Les opérations de sauvegarde qui sont démarrées dans cette fenêtre de temps, mais dépassent la durée de la fenêtre ne seront pas annulées.  
  
 @log_backup_freq  
 Ce paramètre détermine la fréquence des sauvegardes de fichier journal. Ces sauvegardes sont effectuées à intervalles réguliers, plutôt que sur la planification spécifiée pour les sauvegardes de base de données. @log_backup_freq peut être en minutes ou heures, et 0 est valide, ce qui n’indique aucune sauvegarde du journal. La désactivation de sauvegardes du journal ne serait appropriée pour les bases de données avec un modèle de récupération simple.  
  
> [!NOTE]  
>  Si le mode de récupération change de simple à complet, vous devez reconfigurer le log_backup_freq à partir de 0 à une valeur différente de zéro.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance au **db_backupoperator** rôle, de base de données avec **ALTER ANY CREDENTIAL** autorisations, et **EXECUTE** autorisations sur **sp_delete_ backuphistory** procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
