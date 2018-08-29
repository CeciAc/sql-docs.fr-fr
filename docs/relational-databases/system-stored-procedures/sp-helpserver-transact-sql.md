---
title: sp_helpserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpserver
- sp_helpserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpserver
ms.assetid: e8f42de7-c738-41c3-8bf5-dbd559dc7184
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5252f299a0d542fe2f91f75d658ff63aec980712
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43038632"
---
# <a name="sphelpserver-transact-sql"></a>sp_helpserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur un serveur distant, sur un serveur de réplication particulier ou sur tous les serveurs des deux types. Fournit le nom du serveur, le nom réseau du serveur, l'état de réplication du serveur, le numéro d'identification du serveur et le nom du classement. Fournit également les valeurs des délais d'expiration pour les connexions ou les requêtes des serveurs liés.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpserver [ [ @server = ] 'server' ]   
  [ , [ @optname = ] 'option' ]   
  [ , [ @show_topology = ] 'show_topology' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@server =** ] **'***server***»**  
 Serveur sur lequel sont fournies les informations. Lorsque *server* n’est pas spécifié, des rapports sur tous les serveurs de **master.sys.servers**. *serveur* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@optname =** ] **'***option***'**  
 Option qui décrit le serveur. *option* est **varchar (** 35 **)**, avec NULL comme valeur par défaut et doit être une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**compatible avec le classement**|Affecte l'exécution des requêtes distribuées sur les serveurs liés. Si cette option a la valeur true,|  
|**accès aux données**|Active ou désactive un serveur lié pour l'accès des requêtes distribuées.|  
|**serveur de distribution**|Serveur de distribution.|  
|**dpub**|Serveur de publication distant de ce serveur de distribution.|  
|**validation de schéma différée**|La vérification du schéma des tables distantes est ignorée au début de la requête.|  
|**pub**|Serveur de publication.|  
|**rpc**|Active l'appel de procédure à distance (RPC) à partir du serveur spécifié.|  
|**sortie RPC**|Active l'appel de procédure à distance (RPC) à destination du serveur spécifié.|  
|**sub**|Abonné.|  
|**system**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**utiliser le classement distant**|Le classement d'une colonne distante est utilisé à la place de celui du serveur local.|  
  
 [  **@show_topology =** ] **'***afficher_la_topologie***'**  
 Relation entre le serveur spécifié et d'autres serveurs. *afficher_la_topologie* est **varchar (** 1 **)**, avec NULL comme valeur par défaut. Si *afficher_la_topologie* n’est pas égal à **t** ou est NULL, **sp_helpserver** renvoie les colonnes figurant dans la section jeux de résultats. Si *afficher_la_topologie* est égal à **t**, outre les colonnes répertoriées dans les jeux de résultats, **sp_helpserver** retourne également **topy** et **topy** plus d’informations.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou 1 (échec).  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du serveur.|  
|**network_name**|**sysname**|Nom réseau du serveur.|  
|**status**|**varchar (** 70 **)**|État du serveur.|  
|**id**|**char (** 4 **)**|Numéro d'identification du serveur.|  
|**collation_name**|**sysname**|Classement du serveur.|  
|**connect_timeout**|**Int**|Valeur du délai d'expiration de la connexion au serveur lié.|  
|**query_timeout**|**Int**|Valeur du délai d'expiration des requêtes sur le serveur lié.|  
  
## <a name="remarks"></a>Notes  
 Un même serveur peut avoir plusieurs états.  
  
## <a name="permissions"></a>Permissions  
 Sans les autorisations sont vérifiées.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-displaying-information-about-all-servers"></a>A. Affichage d’informations sur tous les serveurs  
 L'exemple suivant affiche des informations sur tous les serveurs en utilisant la procédure `sp_helpserver` sans paramètre.  
  
```  
USE master;  
GO  
EXEC sp_helpserver;  
```  
  
### <a name="b-displaying-information-about-a-specific-server"></a>B. Affichage d'informations sur un serveur spécifique  
 Cet exemple affiche toutes les informations sur le serveur `SEATTLE2`.  
  
```  
USE master;  
GO  
EXEC sp_helpserver 'SEATTLE2';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_addsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
