---
title: sp_update_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_schedule
- sp_update_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_schedule
ms.assetid: 97b3119b-e43e-447a-bbfb-0b5499e2fefe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 51e21d189a9302c2dc7b74a013846460e9cb7bc5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946644"
---
# <a name="spupdateschedule-transact-sql"></a>sp_update_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les paramètres d'une planification de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_update_schedule   
    {   [ @schedule_id = ] schedule_id   
      | [ @name = ] 'schedule_name' }  
    [ , [ @new_name = ] new_name ]  
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @schedule_id = ] schedule_id` Identificateur de la planification à modifier. *id_de_la_planification* est **int**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* doit être spécifié.  
  
`[ @name = ] 'schedule_name'` Le nom de la planification à modifier. *nom_de_la_planification*est **sysname**, sans valeur par défaut. Soit *id_de_la_planification* ou *nom_de_la_planification* doit être spécifié.  
  
`[ @new_name = ] new_name` Le nouveau nom pour la planification. *new_name* est **sysname**, avec NULL comme valeur par défaut. Lorsque *nouveau_nom* est NULL, le nom de la planification reste inchangé.  
  
`[ @enabled = ] enabled` Indique l’état actuel de la planification. *activé*est **tinyint**, avec une valeur par défaut **1** (activé). Si **0**, la planification n’est pas activée. Si la planification n'est pas activée, aucun travail n'est exécuté dans cette dernière.  
  
`[ @freq_type = ] freq_type` Une valeur qui indique quand un travail doit être exécuté. *freq_type*est **int**, avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**4**|Tous les jours|  
|**8**|Semaine|  
|**16**|Mois|  
|**32**|Mensuelle, relatif à *freq_interval.*|  
|**64**|Lancé au démarrage du service SQLServerAgent|  
|**128**|Exécution pendant une période d'inactivité de l'ordinateur.|  
  
`[ @freq_interval = ] freq_interval` Les jours d’exécution du travail. *freq_interval* est **int**, avec une valeur par défaut **0**et dépend de la valeur de *freq_type*.  
  
|Valeur de *freq_type*|Effet sur *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (une fois)|*freq_interval* n’est pas utilisé.|  
|**4** (quotidienne)|Chaque *freq_interval* jours.|  
|**8** (hebdomadaire)|*freq_interval* prend une ou plusieurs des opérations suivantes (combinées avec un **OR** opérateur logique) :<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **4** = mardi<br /><br /> **8** = mercredi<br /><br /> **16** = jeudi<br /><br /> **32** = vendredi<br /><br /> **64** = samedi|  
|**16** (mensuellement)|Sur le *freq_interval* jour du mois.|  
|**32** (mensuel relatif)|*freq_interval* est une des opérations suivantes :<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **3** = mardi<br /><br /> **4** = mercredi<br /><br /> **5** = jeudi<br /><br /> **6** = vendredi<br /><br /> **7** = samedi<br /><br /> **8** = jour<br /><br /> **9** = jour de semaine<br /><br /> **10** = jour de week-end|  
|**64** (démarrage de service SQLServerAgent)|*freq_interval* n’est pas utilisé.|  
|**128**|*freq_interval* n’est pas utilisé.|  
  
`[ @freq_subday_type = ] freq_subday_type` Spécifie les unités pour *freq_subday_interval **.* *freq_subday_type*est **int**, avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description (unité)|  
|-----------|--------------------------|  
|**0x1**|À une heure spécifiée|  
|**0x2**|Secondes|  
|**0x4**|Minutes|  
|**0x8**|Heures|  
  
`[ @freq_subday_interval = ] freq_subday_interval` Le nombre de *freq_subday_type* périodes entre chaque exécution d’un travail. *freq_subday_interval*est **int**, avec une valeur par défaut **0**.  
  
`[ @freq_relative_interval = ] freq_relative_interval` Occurrence d’un travail de *freq_interval* chaque mois, si *freq_interval* est **32** (fréquence mensuelle relative). *freq_relative_interval*est **int**, avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description (unité)|  
|-----------|--------------------------|  
|**1**|Première|  
|**2**|Seconde|  
|**4**|Troisième|  
|**8**|Quatrième|  
|**16**|Dernière|  
  
`[ @freq_recurrence_factor = ] freq_recurrence_factor` Le nombre de semaines ou de mois entre chaque exécution d’une tâche planifiée. *freq_recurrence_factor* est utilisé uniquement si *freq_type* est **8**, **16**, ou **32**. *freq_recurrence_factor*est **int**, avec une valeur par défaut **0**.  
  
`[ @active_start_date = ] active_start_date` La date à laquelle l’exécution d’un travail peut commencer. *active_start_date*est **int**, avec NULL comme valeur par défaut, ce qui indique la date d’aujourd'hui. La date est au format AAAAMMJJ. Si *active_start_date* n’est pas NULL, la date doit être supérieure ou égale à 19900101.  
  
 Après avoir créé la planification, examinez la date de début et assurez-vous qu'elle est correcte. Pour plus d’informations, consultez la section « Planification des Date de début » dans [créer et attacher les planifications de travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
`[ @active_end_date = ] active_end_date` La date à laquelle l’exécution d’un travail peut s’arrêter. *active_end_date*est **int**, avec une valeur par défaut **99991231**, ce qui indique le 31 décembre 9999. La mise en forme est la suivante : AAAAMMJJ.  
  
`[ @active_start_time = ] active_start_time` L’heure sur n’importe quel jour entre *active_start_date* et *active_end_date* pour commencer l’exécution d’un travail. *heure_de_début_active*est **int**, avec une valeur par défaut 000000, ce qui indique 12:00:00 a.m. sur une horloge de 24 heures. Elle doit être au format HHMMSS.  
  
`[ @active_end_time = ] active_end_time` L’heure sur n’importe quel jour entre *active_start_date* et *active_end_date* pour arrêter l’exécution d’un travail. *heure_fin_active*est **int**, avec une valeur par défaut **235959**, ce qui indique à 11:59:59 P.M. sur une horloge de 24 heures. Elle doit être au format HHMMSS.  
  
`[ @owner_login_name = ] 'owner_login_name']` Le nom du principal de serveur qui détient la planification. *owner_login_name* est **sysname**, avec NULL comme valeur par défaut, ce qui indique que la planification est détenue par le créateur.  
  
`[ @automatic_post = ] automatic_post` Réservé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Tous les travaux qui utilisent la planification utilisent immédiatement les nouveaux paramètres. Cependant, la modification d'une planification n'entraîne pas l'arrêt des travaux en cours d'exécution.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Seuls les membres du **sysadmin** peut modifier une planification détenue par un autre utilisateur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre comment changer l'état activé de la planification `NightlyJobs` en `0` et comment définir le propriétaire à `terrid`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_schedule  
    @name = 'NightlyJobs',  
    @enabled = 0,  
    @owner_login_name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Planifier un travail](../../ssms/agent/schedule-a-job.md)   
 [Créer une planification](../../ssms/agent/create-a-schedule.md)   
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
