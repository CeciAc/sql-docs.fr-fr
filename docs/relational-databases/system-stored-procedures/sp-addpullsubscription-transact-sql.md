---
title: sp_addpullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription
- sp_addpullsubscription_TSQL
helpviewer_keywords:
- sp_addpullsubscription
ms.assetid: 0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f65d868f7560f1e413b8c28308afac495233102
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769079"
---
# <a name="spaddpullsubscription-transact-sql"></a>sp_addpullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données du serveur de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut. *publisher_db* est ignoré par les serveurs de publication Oracle.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @independent_agent = ] 'independent_agent'`Spécifie s’il existe un Agent de distribution autonome pour cette publication. *independent_agent* est de type **nvarchar (5)** , avec true comme valeur par défaut. Si la **valeur est true**, il existe un agent de distribution autonome pour cette publication. Si la **valeur**est false, il existe un agent de distribution pour chaque paire base de données de la base de données du serveur de publication/abonné. *independent_agent* est une propriété de la publication et doit avoir la même valeur ici que sur le serveur de publication.  
  
`[ @subscription_type = ] 'subscription_type'`Type d’abonnement. *subscription_type* est de type **nvarchar (9)** , avec **anonymous**comme valeur par défaut. Vous devez spécifier la valeur **pull** pour *subscription_type*, à moins que vous ne souhaitiez créer un abonnement sans enregistrer l’abonnement sur le serveur de publication. Dans ce cas, vous devez spécifier une valeur **anonyme**. Cela s'avère nécessaire lorsque vous ne pouvez pas établir de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le serveur de publication pendant la configuration de l'abonnement.  
  
`[ @description = ] 'description'`Description de la publication. *Description* est de type **nvarchar (100)** , avec NULL comme valeur par défaut.  
  
`[ @update_mode = ] 'update_mode'`Type de mise à jour. *update_mode* est de type **nvarchar (30)** et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**lecture seule** valeurs|L'abonnement est en lecture seule. Aucune modification effectuée sur l'Abonné ne sera retournée au serveur de publication. Cette valeur doit être utilisée si aucune mise à jour ne doit être effectuée sur le serveur de publication.|  
|**synctran**|Active la prise en charge des abonnements de mise à jour immédiate.|  
|**TRAN en file d’attente**|Active l'abonnement pour la mise à jour en attente. Les modifications de données peuvent être effectuées chez l'abonné, stockées dans une file d'attente, puis propagées vers le serveur de publication.|  
|**failover**|Active l'abonnement pour la mise à jour immédiate avec mise à jour en attente sous forme de basculement. Les modifications de données peuvent être effectuées chez l'abonné, puis propagées immédiatement vers le serveur de publication. Si le serveur de publication et l'Abonné ne sont pas connectés, les modifications de données effectuées chez l'Abonné peuvent être stockées dans une file d'attente jusqu'à ce que l'Abonné et le serveur de publication soient reconnectés.|  
|**basculement en file d’attente**|Active l'abonnement en tant qu'abonnement de mise à jour en attente, avec possibilité de passer au mode de mise à jour immédiate. Les modifications de données peuvent être effectuées chez l'abonné et stockées dans une file d'attente, jusqu'à ce qu'une connexion soit établie entre l'abonné et le serveur de publication. Lorsqu'une connexion permanente est établie, il est possible de passer au mode de mise à jour immédiate. *Non pris en charge pour les serveurs de publication Oracle*.|  
  
`[ @immediate_sync = ] immediate_sync`Indique si les fichiers de synchronisation sont créés ou recréés à chaque exécution du Agent d’instantané. *immediate_sync* est de **bits** avec 1 comme valeur par défaut et doit être défini sur la même valeur que *immediate_sync* dans **sp_addpublication**. *immediate_sync* est une propriété de la publication et doit avoir la même valeur ici que sur le serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addpullsubscription** est utilisé dans la réplication d’instantané et la réplication transactionnelle.  
  
> [!IMPORTANT]  
>  Pour les abonnements mis à jour en attente, utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les connexions aux abonnés et spécifiez un compte différent pour la connexion à chaque abonné. Lors de la création d'un abonnement par extraction de données prenant en charge la mise à jour en attente, la réplication configure toujours la connexion de manière à ce qu'elle utilise l'authentification Windows (pour les abonnements par extraction de données, la réplication ne peut pas accéder aux métadonnées de l'Abonné qui sont requises pour utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Dans ce cas, vous devez exécuter [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) pour modifier la connexion afin d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliser l’authentification après la configuration de l’abonnement.  
  
 Si la [table &#40;Transact-SQL&#41; MSreplication_subscriptions](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) n’existe pas sur l’abonné, **sp_addpullsubscription** la crée. Elle ajoute également une ligne à la [table &#40;Transact-SQL&#41; MSreplication_subscriptions](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) . Pour les abonnements par extraction, [ &#40;sp_addsubscription&#41; Transact-SQL](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) doit d’abord être appelée sur le serveur de publication.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-t_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_addpullsubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement par extraction de données ](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
