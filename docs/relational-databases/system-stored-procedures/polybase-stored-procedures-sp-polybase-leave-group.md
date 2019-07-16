---
title: sp_polybase_leave_group (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
author: rothja
ms.author: jroth
ms.openlocfilehash: 0071746f2d65dd0c9c699beeacf404bf3dd7bb65
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941925"
---
# <a name="sppolybaseleavegroup-transact-sql"></a>sp_polybase_leave_group (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Supprime une instance de SQL Server à partir d’un groupe PolyBase pour le calcul de la montée en puissance. 
 
 L’instance de SQL Server doit posséder le [PolyBase Guide](../../relational-databases/polybase/polybase-guide.md) fonctionnalité installée.  PolyBase permet l’intégration de sources de données non-SQL Server, telles que Hadoop et Azure stockage d’objets blob. Voir aussi [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation CONTROL SERVER.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez uniquement supprimer un nœud de calcul d’un groupe.  
  
 Après avoir exécuté la procédure stockée, redémarrez le moteur PolyBase et du PolyBase Data Movement Service sur l’ordinateur. Pour vérifier exécutez la DMV suivante sur le nœud principal : **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Exemple  
 L’exemple supprime l’ordinateur actuel à partir d’un groupe PolyBase.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
