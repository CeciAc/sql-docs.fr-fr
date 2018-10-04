---
title: sp_update_alert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_alert_TSQL
- sp_update_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_alert
ms.assetid: 4bbaeaab-8aca-4c9e-abc1-82ce73090bd3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24cd1864fc31524dcd661cd9eb108d8cb4fa1b77
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846727"
---
# <a name="spupdatealert-transact-sql"></a>sp_update_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met à jour les paramètres d'une alerte existante.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_update_alert   
     [ @name =] 'name'   
     [ , [ @new_name =] 'new_name']   
     [ , [ @enabled =] enabled]   
     [ , [ @message_id =] message_id]   
     [ , [ @severity =] severity]   
     [ , [ @delay_between_responses =] delay_between_responses]   
     [ , [ @notification_message =] 'notification_message']   
     [ , [ @include_event_description_in =] include_event_description_in]   
     [ , [ @database_name =] 'database']   
     [ , [ @event_description_keyword =] 'event_description_keyword']   
     [ , [ @job_id =] job_id | [@job_name =] 'job_name']   
     [ , [ @occurrence_count = ] occurrence_count]   
     [ , [ @count_reset_date =] count_reset_date]   
     [ , [ @count_reset_time =] count_reset_time]   
     [ , [ @last_occurrence_date =] last_occurrence_date]   
     [ , [ @last_occurrence_time =] last_occurrence_time]   
     [ , [ @last_response_date =] last_response_date]   
     [ , [ @last_response_time =] last_response _time]  
     [ , [ @raise_snmp_trap =] raise_snmp_trap]  
     [ , [ @performance_condition =] 'performance_condition' ]   
     [ , [ @category_name =] 'category']  
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@name =**] **'***nom***'**  
 Nom de l'alerte devant être mise à jour. *nom* est **sysname**, sans valeur par défaut.  
  
 [  **@new_name =**] **'***nouveau_nom***'**  
 Nouveau nom de l'alerte. Le nom doit être unique. *new_name* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@enabled =**] *activé*  
 Spécifie si l’alerte est activée (**1**) ou désactivée (**0**). *activé* est **tinyint**, avec NULL comme valeur par défaut. Pour pouvoir se déclencher, une alerte doit être activée.  
  
 [ **@message_id =**] *message_id*  
 Nouveau message ou numéro d'erreur pour la définition de l'alerte. En règle générale, *message_id* correspond à un numéro d’erreur dans le **sysmessages** table. *message_id* est **int**, avec NULL comme valeur par défaut. Un message ID peut être utilisé uniquement si le paramètre de niveau de gravité de l’alerte est **0**.  
  
 [  **@severity =**] *gravité*  
 Un nouveau niveau de gravité (à partir de **1** via **25**) pour la définition d’alerte. N’importe quel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message envoyé dans le journal des applications Windows avec la gravité indiquée Active l’alerte. *gravité* est **int**, avec NULL comme valeur par défaut. Un niveau de gravité peut être utilisé uniquement si le paramètre d’ID de message pour l’alerte est **0**.  
  
 [  **@delay_between_responses =**] *délai_entre_réponses*  
 Nouveau délai d'attente, en secondes, entre les réponses faisant suite au déclenchement de l'alerte. *délai_entre_réponses* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@notification_message =**] **'***message_notification***'**  
 Texte révisé d’un message supplémentaire envoyé à l’opérateur en tant que partie du message électronique, **envoi réseau**, ou par radiomessagerie. *message_notification* est **nvarchar (512)**, avec NULL comme valeur par défaut.  
  
 [ **@include_event_description_in =**] *include_event_description_in*  
 Indique si la description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des applications Windows doit être incluse dans le message de notification. *inclure_description_événement_dans* est **tinyint**, avec NULL comme valeur par défaut et peut prendre l’une ou plusieurs des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|None|  
|**1**|Messagerie électronique|  
|**2**|Radiomessagerie|  
|**4**|**net send**|  
|**7**|All|  
  
 [  **@database_name =**] **'***base de données***'**  
 Nom de la base de données dans laquelle l'erreur doit survenir pour que l'alerte soit déclenchée. *base de données* est **sysname.** Les noms placés entre crochets ([ ]) ne sont pas autorisés. La valeur par défaut est NULL.  
  
 [ **@event_description_keyword =**] **'***event_description_keyword***'**  
 Chaîne de caractères devant figurer dans la description de l'erreur dans le journal des messages d'erreur. Les caractères correspondant au modèle d'expression [!INCLUDE[tsql](../../includes/tsql-md.md)] LIKE sont admis. *motclé_description_événement* est **nvarchar (100)**, avec NULL comme valeur par défaut. Ce paramètre est utile pour filtrer les noms d’objets (par exemple, **% customer_table %**).  
  
 [  **@job_id =**] *job_id*  
 Numéro d’identification. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut. Si *job_id* est spécifié, *nom_travail* doit être omis.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail exécuté en réponse à l'alerte. *job_name* est **sysname**, avec NULL comme valeur par défaut. Si *nom_travail* est spécifié, *job_id* doit être omis.  
  
 [  **@occurrence_count =** ] *occurrence_count*  
 Réinitialise le nombre de fois que l'alerte s'est produite. *occurrence_count* est **int**, avec NULL comme valeur par défaut et peut être définie uniquement au **0**.  
  
 [ **@count_reset_date =**] *count_reset_date*  
 Réinitialise la date de la dernière réinitialisation du nombre d'occurrences. *date_réinitialisation_compte* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@count_reset_time =**] *heure_réinitialisation_compte*  
 Réinitialise l'heure de la dernière réinitialisation du nombre d'occurrences. *heure_réinitialisation_compte* est **int**, avec NULL comme valeur par défaut.  
  
 [ **@last_occurrence_date =**] *last_occurrence_date*  
 Réinitialise la date de la dernière occurrence de l'alerte. *date_dernière_occurrence* est **int**, avec NULL comme valeur par défaut et peut être définie uniquement au **0**.  
  
 [  **@last_occurrence_time =**] *heure_dernière_occurrence*  
 Réinitialise l'heure de la dernière occurrence de l'alerte. *heure_dernière_occurrence* est **int**, avec NULL comme valeur par défaut et peut être définie uniquement au **0**.  
  
 [ **@last_response_date =**] *last_response_date*  
 Réinitialise la date à laquelle l'alerte a reçu la dernière réponse du service de l'Agent SQL Server. *date_dernière_réponse* est **int**, avec NULL comme valeur par défaut et peut être définie uniquement au **0**.  
  
 [  **@last_response_time =**] *heure_dernière_réponse*  
 Réinitialise l'heure à laquelle l'alerte a reçu la dernière réponse du service de l'Agent SQL Server. *heure_dernière_réponse* est **int**, avec NULL comme valeur par défaut et peut être définie uniquement au **0**.  
  
 [  **@raise_snmp_trap =**] *raise_snmp_trap*  
 Réservé.  
  
 [  **@performance_condition =**] **'***l’argument condition_performances***'**  
 Une valeur exprimée dans le format **'***itemcomparatorvalue***'**. *l’argument condition_performances* est **nvarchar (512)**, avec NULL comme valeur par défaut et se compose de ces éléments.  
  
|Élément de format|Description|  
|--------------------|-----------------|  
|*Élément*|Objet de performances, compteur de performances ou instance nommée du compteur.|  
|*Comparateur*|Un de ces opérateurs : **>**, **<**, **=**|  
|*Value*|Valeur numérique du compteur.|  
  
 [  **@category_name =**] **'***catégorie***'**  
 Nom de la catégorie d'alerte. *catégorie* est **sysname** avec NULL comme valeur par défaut.  
  
 [ **@wmi_namespace**=] **'***wmi_namespace***'**  
 Espace de noms WMI permettant de rechercher des événements via des requêtes. *wmi_namespace* est **sysname**, avec NULL comme valeur par défaut.  
  
 [ **@wmi_query**=] **'***wmi_query***'**  
 Requête spécifiant l'événement WMI pour l'alerte. *wmi_query* est **nvarchar (512)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Uniquement **sysmessages** écrites dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] journal des applications Windows peut déclencher une alerte.  
  
 **sp_update_alert** modifie uniquement les paramètres d’alerte pour le paramètre auquel les valeurs sont fournies. Si un paramètre est manquant, la valeur actuelle est retenue.  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette procédure stockée, les utilisateurs doivent être un membre de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant modifie le paramètre activé depuis `Test Alert` à `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_alert  
    @name = N'Test Alert',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
