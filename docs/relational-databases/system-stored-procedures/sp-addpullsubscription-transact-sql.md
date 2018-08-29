---
title: sp_addpullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
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
- sp_addpullsubscription
- sp_addpullsubscription_TSQL
helpviewer_keywords:
- sp_addpullsubscription
ms.assetid: 0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23ca38b8d3618a77ccd6af03be6525cd5f65dbe6
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033882"
---
# <a name="spaddpullsubscription-transact-sql"></a>sp_addpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un abonnement par extraction de données à une publication transactionnelle ou d'instantané. Cette procédure stockée est exécutée sur la base de données de l'Abonné dans laquelle l'abonnement extrait doit être créé.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addpullsubscription [ @publisher= ] 'publisher'  
    [ , [ @publisher_db= ] 'publisher_db' ]  
        , [ @publication= ] 'publication'  
    [ , [ @independent_agent= ] 'independent_agent' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @update_mode= ] 'update_mode' ]  
    [ , [ @immediate_sync = ] immediate_sync ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publisher=**] **'***publisher***'**  
 Nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nom de la base de données du serveur de publication. *publisher_db* est **sysname**, avec NULL comme valeur par défaut. *publisher_db* est ignoré par les serveurs de publication Oracle.  
  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@independent_agent=**] **'***independent_agent***'**  
 Spécifie s'il existe une version autonome de l'Agent de distribution pour cette publication *independent_agent* est **nvarchar (5)**, avec TRUE comme valeur par défaut. Si **true**, il existe un Agent de Distribution autonome pour cette publication. Si **false**, il existe un Agent de Distribution pour chaque paire de base de données de serveur de publication/abonné de base de données. *independent_agent* est une propriété de la publication et doit avoir la même valeur ici que sur le serveur de publication.  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 Est le type d’abonnement. *subscription_type* est **nvarchar(9)**, avec une valeur par défaut **anonyme**. Vous devez spécifier une valeur de **extraction** pour *subscription_type*, sauf si vous souhaitez créer un abonnement sans l’enregistrer sur le serveur de publication. Dans ce cas, vous devez spécifier une valeur de **anonyme**. Cela est nécessaire pour les cas dans lequel vous ne pouvez pas établir une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion au serveur de publication lors de la configuration de l’abonnement.  
  
 [  **@description=**] **'***description***'**  
 Est la description de la publication. *Description* est **nvarchar (100)**, avec NULL comme valeur par défaut.  
  
 [  **@update_mode=**] **'***update_mode***'**  
 Est le type de mise à jour. *update_mode* est **nvarchar (30)**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**en lecture seule** (valeur par défaut)|L'abonnement est en lecture seule. Aucune modification effectuée sur l'Abonné ne sera retournée au serveur de publication. Cette valeur doit être utilisée si aucune mise à jour ne doit être effectuée sur le serveur de publication.|  
|**synctran**|Active la prise en charge des abonnements de mise à jour immédiate.|  
|**tran en file d’attente**|Active l'abonnement pour la mise à jour en attente. Les modifications de données peuvent être effectuées chez l'abonné, stockées dans une file d'attente, puis propagées vers le serveur de publication.|  
|**basculement**|Active l'abonnement pour la mise à jour immédiate avec mise à jour en attente sous forme de basculement. Les modifications de données peuvent être effectuées chez l'abonné, puis propagées immédiatement vers le serveur de publication. Si le serveur de publication et l'Abonné ne sont pas connectés, les modifications de données effectuées chez l'Abonné peuvent être stockées dans une file d'attente jusqu'à ce que l'Abonné et le serveur de publication soient reconnectés.|  
|**basculement en file d’attente**|Active l'abonnement en tant qu'abonnement de mise à jour en attente, avec possibilité de passer au mode de mise à jour immédiate. Les modifications de données peuvent être effectuées chez l'abonné et stockées dans une file d'attente, jusqu'à ce qu'une connexion soit établie entre l'abonné et le serveur de publication. Lorsqu'une connexion permanente est établie, il est possible de passer au mode de mise à jour immédiate. *Non pris en charge pour les serveurs de publication Oracle*.|  
  
 [  **@immediate_sync =**] *immediate_sync*  
 Est si les fichiers de synchronisation sont créés ou recréés chaque fois que l’Agent d’instantané s’exécute. *immediate_sync* est **bits** avec une valeur par défaut 1 et doit être définie sur la même valeur que *immediate_sync* dans **sp_addpublication**. *immediate_sync* est une propriété de la publication et doit avoir la même valeur ici que sur le serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addpullsubscription** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
> [!IMPORTANT]  
>  Pour les abonnements mis à jour en attente, utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les connexions aux abonnés et spécifiez un compte différent pour la connexion à chaque abonné. Lors de la création d'un abonnement par extraction de données prenant en charge la mise à jour en attente, la réplication configure toujours la connexion de manière à ce qu'elle utilise l'authentification Windows (pour les abonnements par extraction de données, la réplication ne peut pas accéder aux métadonnées de l'Abonné qui sont requises pour utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Dans ce cas, vous devez exécuter [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) pour modifier la connexion à utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification une fois que l’abonnement est configuré.  
  
 Si le [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) table n’existe pas sur l’abonné, **sp_addpullsubscription** le crée. Il ajoute également une ligne à la [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) table. Pour les abonnements extraits, [sp_addsubscription &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) doit être appelée en premier sur le serveur de publication.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-t_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addpullsubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create an Updatable Subscription à une Publication transactionnelle](../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md) [s’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
