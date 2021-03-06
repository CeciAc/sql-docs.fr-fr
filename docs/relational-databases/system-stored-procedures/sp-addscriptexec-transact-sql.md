---
title: sp_addscriptexec (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8ae792ba7f8422e841abbbe2f80b096497df993
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022452"
---
# <a name="spaddscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Publie un script SQL (fichier .sql) sur tous les Abonnés d'une publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @scriptfile = ] 'scriptfile'` Est le chemin d’accès complet au fichier de script SQL. *ScriptFile* est **nvarchar (4000)** , sans valeur par défaut.  
  
`[ @skiperror = ] 'skiperror'` Indique si l’Agent de Distribution ou l’Agent de fusion doit s’arrêter lorsqu’une erreur s’est produite lors du traitement du script. *SkipError* est **bits**, avec 0 comme valeur par défaut.  
  
 **0** = l’agent s’arrête.  
  
 **1** = l’agent continue le script et ignore l’erreur.  
  
`[ @publisher = ] 'publisher'` Spécifie un non - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de la publication à partir d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addscriptexec** est utilisé dans la réplication de fusion et la réplication transactionnelle.  
  
 **sp_addscriptexec** n’est pas utilisé pour la réplication d’instantané.  
  
 Pour utiliser **sp_addscriptexec**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service doit disposer de lecture et d’autorisations en écriture sur les autorisations instantané de l’emplacement et en lecture sur l’emplacement où tous les scripts sont stockées.  
  
 Le [utilitaire sqlcmd](../../tools/sqlcmd-utility.md) est utilisé pour exécuter le script sur l’abonné, et le script est exécuté dans le contexte de sécurité utilisé par l’Agent de Distribution ou l’Agent de fusion lors de la connexion à la base de données d’abonnement. Lorsque l’agent est exécuté sur une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le [utilitaire osql](../../tools/osql-utility.md) est utilisé au lieu de [sqlcmd](../../tools/sqlcmd-utility.md).  
  
 **sp_addscriptexec** est utile dans l’application de scripts pour les abonnés et utilise [sqlcmd](../../tools/sqlcmd-utility.md) pour appliquer le contenu du script à l’abonné. Toutefois, dans la mesure où les configurations des Abonnés peuvent varier, des scripts testés avant la publication sur le serveur de publication peuvent toujours provoquer des erreurs sur un Abonné. *SkipError* fournit la possibilité de l’Agent de Distribution ou l’Agent de fusion ignorer les erreurs et continuer. Utilisez [sqlcmd](../../tools/sqlcmd-utility.md) pour tester les scripts avant d’exécuter **sp_addscriptexec**.  
  
> [!NOTE]  
>  Les erreurs ignorées sont toujours consignées dans l'historique de l'Agent à titre de référence.  
  
 À l’aide de **sp_addscriptexec** pour valider un fichier de script pour les publications utilisant FTP pour la remise d’instantanés est uniquement pris en charge pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addscriptexec**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des Scripts pendant la synchronisation &#40;programmation Transact-SQL&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Synchroniser les données](../../relational-databases/replication/synchronize-data.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
