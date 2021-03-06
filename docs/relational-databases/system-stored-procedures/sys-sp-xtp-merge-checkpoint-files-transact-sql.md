---
title: Sys.sp_xtp_merge_checkpoint_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_merge_checkpoint_files_TSQL
- sys.sp_xtp_merge_checkpoint_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_merge_checkpoint_files
ms.assetid: da04df2a-f7a1-41e7-a1ef-2d5d68919892
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73638d41c7a24a37c068d365771b4d0469a174d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041022"
---
# <a name="sysspxtpmergecheckpointfiles-transact-sql"></a>sys.sp_xtp_merge_checkpoint_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  **Sys.sp_xtp_merge_checkpoint_files** fusionne tous les fichiers de données et delta dans la plage de transactions spécifié.  
  
 Pour plus d’informations, consultez [création et gestion du stockage des objets à mémoire optimisée](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
||  
|-|  
|**Remarque**: Cette procédure stockée est déconseillée dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Il n’est plus nécessaire et ne peut pas être utilisé, en commençant [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_xtp_merge_checkpoint_files database_name, @transaction_lower_bound, @transaction_upper_bound  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données dans laquelle la fusion doit être appelée. Si la base de données ne contient pas de tables en mémoire, cette procédure retourne une erreur utilisateur. Si la base de données est hors connexion, retourne une erreur.  
  
 *lower_bound_Tid*  
 La limite inférieure (bigint) de transactions pour un fichier de données, comme indiqué dans [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) correspondant au fichier de point de contrôle de la fusion. Une erreur est générée pour une valeur transactionId non valide.  
  
 *upper_bound_Tid*  
 La limite supérieure (bigint) de transactions pour un fichier de données, comme indiqué dans [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md). Une erreur est générée pour une valeur transactionId non valide.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Aucun  
  
## <a name="cursors-returned"></a>Curseurs retournés  
 Aucun  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'appartenance au rôle serveur fixe sysadmin et au rôle de base de données fixe db_owner.  
  
## <a name="remarks"></a>Notes  
 Fusionne tous les fichiers de données et delta dans la plage valide pour générer un seul fichier de données et delta. Cette procédure ne respecte pas la stratégie de fusion.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
