---
title: sp_MSchange_distribution_agent_properties (T-SQL)
description: Décrit la procédure stockée sp_MSchange_distribution_agent_properties utilisée pour modifier les propriétés de la Agent de distribution pour une topologie de Réplication SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_distribution_agent_properties
- sp_MSchange_distribution_agent_properties_TSQL
helpviewer_keywords:
- sp_MSchange_distribution_agent_properties
ms.assetid: 7dac5e68-bf84-433a-a531-66921f35126f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a2e2e3c0074c3fcc53298c2556c786c9b7057db
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322263"
---
# <a name="sp_mschange_distribution_agent_properties-transact-sql"></a>sp_MSchange_distribution_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d’un travail de agent de distribution qui s’exécute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sur un serveur de distribution ou version ultérieure. Cette procédure stockée est utilisée pour modifier des propriétés lorsque le serveur de publication s'exécute sur une instance de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_MSchange_distribution_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @property = ] 'property'   
        , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données de publication. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @subscriber = ] 'subscriber'`Nom de l’abonné. *Subscriber* est de **type sysname**, sans valeur par défaut.  
  
`[ @subscriber_db = ] 'subscriber_db'`Nom de la base de données d’abonnement. *subscriber_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @property = ] 'property'`Propriété de publication à modifier. *Property* est de **type sysname**, sans valeur par défaut.  
  
`[ @value = ] 'value'`Nouvelle valeur de la propriété. *value* est de type **nvarchar (524)**, avec NULL comme valeur par défaut.  
  
 Le tableau ci-dessous décrit les propriétés modifiables du travail de l'Agent de distribution et les limites liées aux valeurs de ces propriétés.  
  
|Propriété|Valeur|Description|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Nom de connexion du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent s'exécute.|  
|**distrib_job_password**||Mot de passe du compte Windows sous lequel le travail de l'Agent s'exécute.|  
|**subscriber_catalog**||Catalogue à utiliser lors d’une connexion au fournisseur OLE DB. *Cette propriété n’est valide que pour les abonnés non-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*|  
|**subscriber_datasource**||Nom de la source de données tel qu'il est interprété par le fournisseur OLE DB. *Cette propriété n’est valide que pour les abonnés non-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*|  
|**subscriber_location**||Emplacement de la base de données tel qu’il est interprété par le fournisseur OLE DB. *Cette propriété n’est valide que pour les abonnés non-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*|  
|**subscriber_login**||Nom de connexion à utiliser lors de la connexion à un Abonné pour synchroniser l'abonnement.|  
|**subscriber_password**||Mot de passe de l’abonné.<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**subscriber_provider**||Identificateur de programme unique (PROGID) avec lequel le fournisseur OLE DB de la source de données non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrit. *Cette propriété n’est valide que pour les abonnés non-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*|  
|**subscriber_providerstring**||Chaîne de connexion propre au fournisseur OLE DB qui identifie la source de données. *Cette propriété est uniquement valide pour les Abonnés non-SQL Server.*|  
|**subscriber_security_mode**|**1,0**|Authentification Windows.<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Identification.|  
|**subscriber_type**|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Côté|  
||**1,0**|Serveur de la source de données ODBC.|  
||**1,3**|Fournisseur OLE DB|  
|**SubscriptionStreams**||Indique le nombre de connexions autorisées par Agent de distribution pour appliquer en parallèle des traitements de modifications à un Abonné. *Non pris en charge pour les abonnés non-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les serveurs de *publication Oracle ou les abonnements d’égal à égal.*|  
  
> [!NOTE]  
>  Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_MSchange_distribution_agent_properties** est utilisé dans la réplication d’instantané et la réplication transactionnelle.  
  
 Quand le serveur de publication s’exécute sur [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] une instance de ou version ultérieure, vous devez utiliser [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) pour modifier les propriétés d’un travail agent de fusion qui synchronise un abonnement par émission de notification qui s’exécute sur le serveur de distribution.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution peuvent exécuter **sp_MSchange_distribution_agent_properties**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)  
  
  
