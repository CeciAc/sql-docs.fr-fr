---
title: sp_mergesubscription_cleanup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
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
- sp_mergesubscription_cleanup
- sp_mergesubscription_cleanup_TSQL
helpviewer_keywords:
- sp_mergesubscription_cleanup
ms.assetid: bfad414f-2bda-4bf5-9507-56a1e743dfc4
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3135d0576d09efc2fa00804ab47a2e1a7836dd07
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031201"
---
# <a name="spmergesubscriptioncleanup-transact-sql"></a>sp_mergesubscription_cleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime les métadonnées, telles que des déclencheurs et des entrées, de **sysmergesubscriptions** et **sysmergearticles** après la suppression de l’abonnement de fusion spécifiée sur le serveur de publication. Cette procédure stockée est exécutée sur l’abonné sur la base de données d’abonnement.  
  
> [!NOTE]  
>  Pour un abonnement par extraction, les métadonnées sont supprimées lorsque [sp_dropmergepullsubscription &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md) est exécutée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_mergesubscription_cleanup [ @publisher =] 'publisher'  
        , [ @publisher_db =] 'publisher_db'  
        , [ @publication =] 'publication'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publisher =**] **'***publisher***'**  
 Nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 Nom de la base de données du serveur de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
 [  **@publication =**] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_mergesubscription_cleanup** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_mergesubscription_cleanup**.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer un abonnement envoyé](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_expired_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-expired-subscription-cleanup-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
