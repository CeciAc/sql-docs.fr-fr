---
title: sp_xp_cmdshell_proxy_account (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 59ea64e16f1469c12461a559c3f102094615fa12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950459"
---
# <a name="spxpcmdshellproxyaccount-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crée une information d’identification de proxy pour **xp_cmdshell**.  
  
> [!NOTE]  
>  **xp_cmdshell** est désactivée par défaut. Pour activer **xp_cmdshell**, consultez [Server Configuration Option xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Arguments  
 NULL  
 Indique que les informations d'identification de proxy doivent être supprimées.  
  
 *account_name*  
 Spécifie la connexion Windows qui doit être le proxy.  
  
 *password*  
 Spécifie le mot de passe du compte Windows.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Les informations d’identification de proxy seront appelée **## xp_cmdshell_proxy_account ##** .  
  
 Lorsqu’elle est exécutée à l’aide de l’option NULL, **sp_xp_cmdshell_proxy_account** supprime les informations d’identification de proxy.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-the-proxy-credential"></a>R. Création d'informations d'identification de proxy  
 L'exemple ci-dessous montre comment créer des informations d'identification de proxy pour un compte Windows nommé `ADVWKS\Max04` avec le mot de passe `ds35efg##65`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>B. Suppression des informations d'identification de proxy  
 Dans l'exemple ci-dessous, les informations d'identification de proxy sont supprimées de la banque d'informations d'identification.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [xp_cmdshell &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
