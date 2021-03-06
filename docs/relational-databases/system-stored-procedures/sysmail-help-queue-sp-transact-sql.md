---
title: sysmail_help_queue_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_queue_sp
- sysmail_help_queue_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_queue_sp
ms.assetid: 94840482-112c-4654-b480-9b456c4c2bca
author: stevestein
ms.author: sstein
ms.openlocfilehash: d506d7ea841e211d9ab6fb0715a6a9359cefa83d
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305220"
---
# <a name="sysmail_help_queue_sp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il existe deux files d'attente dans la messagerie de base de données : la file d'attente des messages et la file d'attente des états. La file d'attente des messages stocke les éléments de messagerie en attente d'envoi. La file d'attente des états stocke l'état des éléments qui ont déjà été envoyés. Cette procédure stockée permet d'afficher l'état de la file d'attente des messages ou des états. Si le paramètre **\@queue_type** n’est pas spécifié, la procédure stockée renvoie une ligne pour chacune des files d’attente.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @queue_type = ] 'queue_type'` argument facultatif supprime les messages électroniques du type spécifié en tant que *queue_type*. *queue_type* est de type **nvarchar (6)** et n’a pas de valeur par défaut. Les entrées valides sont **mail** et **Status**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-set"></a>Jeu de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar(6)**|Type de file d'attente. Les valeurs possibles sont **mail** et **Status**.|  
|**length**|**Int**|Nombre d'éléments de messagerie dans la file d'attente spécifiée.|  
|**state**|**nvarchar(64)**|État du moniteur. Les valeurs possibles sont **INactives** (la file d’attente est inactive), **notifiée** (la file d’attente a reçu l’accusé de réception d’une notification) et **RECEIVES_OCCURRING** (file d’attente de réception).|  
|**last_empty_rowset_time**|**DATE/HEURE**|Date et heure à laquelle la file d'attente était vide pour la dernière fois. Format 24 heures et fuseau horaire GMT.|  
|**last_activated_time**|**DATE/HEURE**|Date et heure de la dernière activation de la file d'attente. Format 24 heures et fuseau horaire GMT.|  
  
## <a name="remarks"></a>Notes  
 Lors de la résolution des Database Mail, utilisez **sysmail_help_queue_sp** pour afficher le nombre d’éléments dans la file d’attente, l’état de la file d’attente et la date de la dernière activation.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, seuls les membres du rôle serveur fixe **sysadmin** peuvent accéder à cette procédure.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie la file d'attente des messages ainsi que celle des états.  
  
```  
EXECUTE msdb.dbo.sysmail_help_queue_sp ;  
GO  
```  
  
 Il s'agit d'un exemple de jeu de résultats qui a été remis en forme pour des raisons de longueur.  
  
```  
queue_type length      state              last_empty_rowset_time  last_activated_time  
---------- -------- ------------------ ----------------------- -----------------------  
mail       0        RECEIVES_OCCURRING 2005-10-07 21:14:47.010 2005-10-10 20:52:51.517  
status     0        INACTIVE           2005-10-07 21:04:47.003 2005-10-10 21:04:47.003  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)  
  
  
