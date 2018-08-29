---
title: sp_setnetname (Transact-SQL) | Microsoft Docs
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
- sp_setnetname
- sp_setnetname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 71dcca516c1533c048d424e68d6aaae197d032ba
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024883"
---
# <a name="spsetnetname-transact-sql"></a>sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit les noms de réseau **sys.servers** à leurs noms d’ordinateurs réseau réels pour les instances distantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette procédure peut être utilisée pour activer l'exécution d'appels de procédures stockées distantes à des ordinateurs dont le nom réseau contient des identificateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non valides.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>Arguments  
 **@server = '** *server* **'**  
 Nom du serveur distant tel qu'il est référencé dans la syntaxe RPC codée par l'utilisateur. Exactement une ligne dans **sys.servers** doit déjà exister pour pouvoir utiliser *server*. *server* est de type **sysname**et n'a pas de valeur par défaut.  
  
 **@netname ='** *network_name* **'**  
 Nom réseau de l'ordinateur auquel les appels de procédures stockées distantes sont effectuées. *network_name* est **sysname**, sans valeur par défaut.  
  
 Ce nom doit correspondre au nom d'ordinateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et peut comprendre des caractères non autorisés dans les identificateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Certains appels de procédures stockées distantes à des ordinateurs Windows peuvent rencontrer des problèmes si le nom d'ordinateur contient des identificateurs non valides.  
  
 Les serveurs liés et les serveurs distants résidant dans le même espace de nom, ils ne peuvent pas avoir le même nom. Toutefois, vous pouvez définir un serveur lié et un serveur distant sur un serveur spécifié en affectant des noms différents et à l’aide de **sp_setnetname** pour définir le nom de réseau d’un d’eux au nom réseau du serveur sous-jacent.  
  
```  
--Assume sqlserv2 is actual name of SQL Server   
--database server  
EXEC sp_addlinkedserver 'sqlserv2';  
GO  
EXEC sp_addserver 'rpcserv2';  
GO  
EXEC sp_setnetname 'rpcserv2', 'sqlserv2';  
```  
  
> [!NOTE]  
>  À l’aide de **sp_setnetname** pour pointer un serveur lié sur le serveur local n’est pas pris en charge. Les serveurs référencés de cette manière ne peuvent pas participer à une transaction distribuée.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **sysadmin** et **setupadmin** rôles serveur fixes.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre une séquence d'administration courante utilisée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer des appels de procédures stockées distantes.  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
