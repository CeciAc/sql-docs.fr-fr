---
title: sp_delete_targetserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_targetserver
- sp_delete_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetserver
ms.assetid: cc438701-ad91-419d-9f23-ebc4c548c700
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63b8fdb66b868d7fc0c1c7a83d574bafb92224b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692243"
---
# <a name="spdeletetargetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime le serveur spécifié de la liste des serveurs cibles disponibles.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@server_name=** ] **'***server***»**  
 Nom du serveur qui doit cesser d'être un serveur cible disponible. *serveur* est **nvarchar (30)**, sans valeur par défaut.  
  
 [  **@clear_downloadlist=** ] *clear_downloadlist*  
 Indique s'il faut effacer la liste de téléchargement du serveur cible. *clear_downloadlist* est de type **bits**, avec une valeur par défaut **1**. Lorsque *clear_downloadlist* est **1**, la procédure efface la liste de téléchargement pour le serveur avant de supprimer le serveur. Lorsque *clear_downloadlist* est **0**, la liste de téléchargement n’est pas effacée.  
  
 [  **@post_defection=** ] *post_defection*  
 Indique s'il faut publier une instruction de désinscription sur le serveur cible. *post_defection* est de type **bits**, avec 1 comme valeur par défaut. Lorsque *post_defection* est **1**, la procédure publie une instruction de désinscription sur le serveur cible avant de supprimer le serveur. Lorsque *post_defection* est **0**, la procédure n’envoie pas d’une instruction de désinscription au serveur cible.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Pour supprimer un serveur cible normalement consiste à appeler **sp_msx_defect** sur le serveur cible. Utilisez **sp_delete_targetserver** uniquement lorsqu’une désinscription manuelle est nécessaire.  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette procédure stockée, les utilisateurs doivent avoir le **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous supprime le serveur `LONDON1` de la liste des serveurs de travail disponibles.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_help_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
