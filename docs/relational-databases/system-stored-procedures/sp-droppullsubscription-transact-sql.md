---
title: sp_droppullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
author: stevestein
ms.author: sstein
ms.openlocfilehash: f4ad522c13987f7617def29d5ff112a5a26db8b9
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771450"
---
# <a name="sp_droppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Supprime un abonnement à la base de données en cours de l'Abonné. Cette procédure stockée est exécutée sur la base de données d'abonnement par extraction de données (pull) de l'abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur distant. *Publisher* est de **type sysname**, sans valeur par défaut. Si la **totalité**est, l’abonnement est supprimé de tous les serveurs de publication.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données du serveur de publication. *publisher_db* est de **type sysname**, sans valeur par défaut. **All** signifie toutes les bases de données du serveur de publication.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut. Si la valeur est **All**, l’abonnement est déposé dans toutes les publications.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 la procédure pas à pas est utilisée dans la réplication d’instantané et la réplication transactionnelle.  
  
 la table de l’éditeur supprime la ligne correspondante dans la table [Transact-SQL &#40;&#41; MSreplication_subscriptions](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) et l’agent de distribution correspondant sur l’abonné. Si aucune ligne n’est laissée dans le champ [MSreplication_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md), elle supprime la table.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou de l’utilisateur qui a créé l’abonnement parextraction peuvent exécuter la fonction la licence. Le rôle de base de données fixe **db_owner** ne peut exécuter la valeur de la base de au cas que si l’utilisateur qui a créé l’abonnement par extraction de données appartient à ce rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer un abonnement par extraction](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
