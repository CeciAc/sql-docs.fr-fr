---
title: sp_help_agent_default (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_help_agent_default
- sp_help_agent_default_TSQL
helpviewer_keywords:
- sp_help_agent_default
ms.assetid: 7ba55e39-05dd-43c7-b5da-b268ed8426dd
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a835b1bafa037e249450118cb08f3d886bb6283b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017815"
---
# <a name="sphelpagentdefault-transact-sql"></a>sp_help_agent_default (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Récupère l'ID de la configuration par défaut du type d'Agent passé en paramètre. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_agent_default [ @profile_id= ] profile_id OUTPUT   
        , [ @agent_type = ] agent_type  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@profile_id=**] *profile_id *** sortie**  
 Identificateur de la configuration par défaut du type d'Agent. *profile_id* est **int**, sans valeur par défaut. *profile_id* est également un paramètre de sortie qui retourne l’ID de la configuration par défaut pour le type d’agent.  
  
 [  **@agent_type=**] **'***agent_type***'**  
 Type de l'Agent. *agent_type* est **int**, sans valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Agent d’instantané.|  
|**2**|Agent de lecture du journal|  
|**3**|Agent de distribution.|  
|**4**|Agent de fusion.|  
|**9**|Agent de lecture de la file d'attente|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_help_agent_default** est utilisée dans tous les types de réplication.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **replmonitor** rôle de base de données fixe peuvent exécuter **sp_help_agent_default**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
