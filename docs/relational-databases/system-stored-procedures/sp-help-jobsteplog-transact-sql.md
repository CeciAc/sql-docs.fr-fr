---
title: sp_help_jobsteplog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 905386a1e346ed982c3ad84baf57f532aa5b020f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828357"
---
# <a name="sphelpjobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les métadonnées spécifiques à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] journal d’étapes de travail de l’Agent. **sp_help_jobsteplog** ne retourne pas le journal réel.  

  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id =**] **'***job_id***'**  
 Numéro d'identification du travail pour lequel renvoyer des informations du journal d'étapes de travail. *job_id* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [ **@step_id =**] *step_id*  
 Numéro d'identification de l'étape du travail. S'il n'est pas inclus, toutes les étapes du travail sont englobées. *l’argument id_étape* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@step_name =**] **'***nom_de_l***'**  
 Nom de l'étape du travail. *nom_de_l* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Identificateur unique de la tâche.|  
|**job_name**|**sysname**|Nom du travail.|  
|**step_id**|**Int**|Identificateur de l'étape du travail. Par exemple, si l’étape est la première étape du travail, son *id_de_l* est 1.|  
|**step_name**|**sysname**|Nom de l’étape du travail.|  
|**step_uid**|**uniqueidentifier**|Identificateur unique de l'étape du travail (généré par le système).|  
|**date_created**|**datetime**|Date de création de l'étape.|  
|**date_modified**|**datetime**|Date de la dernière modification de l'étape.|  
|**log_size**|**float**|Taille du journal d'étapes du travail, en mégaoctets (Mo).|  
|**log**|**nvarchar(max)**|Sortie du journal d'étapes du travail.|  
  
## <a name="remarks"></a>Notes  
 **sp_help_jobsteplog** est dans le **msdb** base de données.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** peuvent uniquement afficher les étapes de travail qu’ils possèdent les métadonnées de journal étape du travail.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. Retourne des informations sur toutes les étapes d'un travail spécifique  
 L'exemple ci-dessous retourne toutes les informations du journal d'étapes du travail `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>B. Retourne des informations sur une étape spécifique du travail  
 L'exemple ci-dessous retourne des informations du journal d'étapes concernant la première étape du travail appelé `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
