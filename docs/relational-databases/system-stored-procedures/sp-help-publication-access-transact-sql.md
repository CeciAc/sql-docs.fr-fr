---
title: sp_help_publication_access (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7c562c039b65f99f1d3d9915f0dd00b93dc95860
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770992"
---
# <a name="sphelppublicationaccess-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne la liste de toutes les connexions accordées pour une publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_publication_access [ @publication = ] 'publication'  
    [ , [ @return_granted = ] 'return_granted' ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @initial_list = ] initial_list ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication à laquelle accéder. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @return_granted = ] 'return_granted'`ID de connexion. *return_granted* est de **bits**, avec 1 comme valeur par défaut. Si la **valeur 0** est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiée et que l’authentification est utilisée, les connexions disponibles qui s’affichent sur le serveur de publication mais pas sur le serveur de distribution sont retournées. Si la **valeur 0** est spécifiée et que l’authentification Windows est utilisée, les connexions qui n’ont pas spécifiquement refusé l’accès au serveur de publication ou au serveur de distribution sont retournées.  
  
`[ @login = ] 'login'`ID de connexion de sécurité standard. *login* est de **%** **type sysname**, avec la valeur par défaut.  
  
`[ @initial_list = ] initial_list`Spécifie s’il faut retourner tous les membres avec un accès à la publication ou uniquement ceux qui ont accès avant l’ajout de nouveaux membres à la liste. *initial_list* est de valeur de bit, avec **0**comme valeur par défaut.  
  
 **1** retourne des informations pour tous les membres du rôle serveur fixe **sysadmin** avec des connexions valides sur le serveur de distribution qui existaient lors de la création de la publication, ainsi que la connexion actuelle.  
  
 **0** retourne des informations pour tous les membres du rôle serveur fixe **sysadmin** avec des connexions valides sur le serveur de distribution qui existaient lors de la création de la publication, ainsi que tous les utilisateurs de la liste d’accès à la publication qui n’appartiennent pas à l' **administrateur système.** rôle serveur fixe.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**nvarchar (256)**|Nom de connexion réel.|  
|**Isntname**|**int**|**0** = la connexion n’est pas un utilisateur Windows.<br /><br /> **1** = la connexion est un utilisateur Windows.|  
|**Isntgroup**|**Int**|**0** = la connexion n’est pas un groupe Windows.<br /><br /> **1** = la connexion est un groupe Windows.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_help_publication_access** est utilisé dans tous les types de réplications.  
  
 Quand **Isntname** et **Isntgroup** dans le jeu de résultats sont **0**, il est supposé que la connexion est une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_help_publication_access**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_grant_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
