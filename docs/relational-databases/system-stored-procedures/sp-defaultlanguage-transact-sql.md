---
title: sp_defaultlanguage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultlanguage
- sp_defaultlanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultlanguage
ms.assetid: 908d01cc-e704-45d9-9e85-d2df6da3e6f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: af2402ce4f1e49ee572a9d271497c2798d679070
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120092"
---
# <a name="spdefaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie la langue par défaut d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @loginame = ] 'login'` Est le nom de connexion. *connexion* est **sysname**, sans valeur par défaut. *connexion* peut être un existant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou un utilisateur de Windows ou un groupe.  
  
`[ @language = ] 'language'` Est la langue par défaut de la connexion. *langage* est **sysname**, avec NULL comme valeur par défaut. *langage* doit être une langue valide sur le serveur. Si *langage* n’est pas spécifié, *langage* est définie sur la langue par défaut du serveur ; langue par défaut est définie par le **sp_configure** variable de configuration **langue par défaut**. Le changement de la langue par défaut du serveur n'affecte pas la langue par défaut des connexions existantes.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_defaultlanguage** appelle ALTER LOGIN, qui prend en charge des options supplémentaires. Pour plus d’informations sur la modification des autres valeurs par défaut de la connexion, consultez [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 Utilisez l'instruction SET LANGUAGE pour modifier la langue de la session active. Utilisez le @@LANGUAGE (fonction) pour afficher le paramètre de langue actuel.  
  
 Si la langue par défaut d'une connexion est supprimée du serveur, cette connexion utilise la langue par défaut du serveur. **sp_defaultlanguage** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
 Pour plus d’informations sur les langues installées sur le serveur sont visibles dans le **sys.syslanguages** vue de catalogue.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER ANY LOGIN.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `ALTER LOGIN` pour changer la langue par défaut de la connexion `Fathima` et choisir l'arabe. Cette méthode est recommandée.  
  
```  
ALTER LOGIN Fathima WITH DEFAULT_LANGUAGE = Arabic;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
