---
title: CREATE EXTERNAL RESOURCE POOL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL RESOURCE POOL
- CREATE EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE POOL
- EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE
- EXTERNAL_RESOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL RESOURCE POOL statement
ms.assetid: 8cc798ad-c395-461c-b7ff-8c561c098808
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7c55041d7b461406305a7b3a17c0e274270b7c5f
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893894"
---
# <a name="create-external-resource-pool-transact-sql"></a>CREATE EXTERNAL RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Crée un pool externe utilisé pour définir des ressources pour les processus externes. Un pool de ressources représente un sous-ensemble des ressources physiques (mémoire et processeurs) d’une instance du moteur de base de données. Le Gouverneur de ressources permet à un administrateur de base de données de répartir des ressources serveur entre plusieurs pools de ressources (64 pools au maximum).

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Pour [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] dans [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], le pool externe gouverne `rterm.exe`, `BxlServer.exe` et les autres processus qu’ils engendrent.
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Pour [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)], le pool externe gouverne `rterm.exe`, `python.exe`, `BxlServer.exe` et les autres processus qu’ils engendrent.
::: moniker-end
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE EXTERNAL RESOURCE POOL pool_name  
[ WITH (  
    [ MAX_CPU_PERCENT = value ]  
    [ [ , ] AFFINITY CPU =    
            {  
                AUTO   
              | ( <cpu_range_spec> )   
              | NUMANODE = ( <NUMA_node_id> )   
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_PROCESSES = value ]   
    )   
]  
[ ; ]  
  
<CPU_range_spec> ::=    
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]  
```  
  
## <a name="arguments"></a>Arguments

*pool_name*  
Nom défini par l’utilisateur du pool de ressources externes. *pool_name* est alphanumérique et peut contenir jusqu'à 128 caractères. Cet argument doit être unique au sein d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et respecter les règles applicables aux [identificateurs](../../relational-databases/databases/database-identifiers.md).  

MAX_CPU_PERCENT =*value*  
Spécifie la bande passante processeur moyenne maximale que toutes les demandes du pool de ressources externes peuvent recevoir en cas de contention du processeur. *value* est un entier. La plage autorisée pour *value* est comprise entre 1 et 100.

AFFINITY {CPU = AUTO | ( \<CPU_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)} Attache le pool de ressources externes à des unités centrales spécifiques.

AFFINITY CPU = **(** \<CPU_range_spec> **)** mappe le pool de ressources externes aux unités centrales [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifiées par les valeurs CPU_ID données.

Quand vous utilisez AFFINITY NUMANODE =  **(** \<NUMA_node_range_spec> **)** , le pool de ressources externes est associé par affinité aux unités centrales physiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correspondant au nœud NUMA ou à la plage de nœuds spécifique. 

MAX_MEMORY_PERCENT =*value*  
Spécifie la mémoire totale du serveur qui peut être utilisée par les demandes dans ce pool de ressources externes. *value* est un entier. La plage autorisée pour *value* est comprise entre 1 et 100.

MAX_PROCESSES =*value*  
Spécifie le nombre maximal de processus autorisés pour le pool de ressources externes. Spécifiez 0 pour définir un seuil illimité pour le pool, qui est alors limité uniquement par les ressources de l’ordinateur.

## <a name="remarks"></a>Notes

[!INCLUDE[ssDE](../../includes/ssde-md.md)] implémente le pool de ressources quand vous exécutez l’instruction [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md).

Pour obtenir des informations générales sur les pools de ressources, consultez [Pool de ressources du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) et [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).

Pour plus d’informations spécifiques à la gestion de pools de ressources externes utilisés pour l’apprentissage automatique, consultez [Gouvernance des ressources de Machine Learning dans SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md). 

## <a name="permissions"></a>Autorisations

Nécessite l'autorisation `CONTROL SERVER`.

## <a name="examples"></a>Exemples

L’instruction suivante définit un pool externe qui limite l’utilisation du processeur à 75 %. L’instruction définit également la mémoire maximale sur 30 % de la mémoire disponible sur l’ordinateur.

```sql
CREATE EXTERNAL RESOURCE POOL ep_1
WITH (  
    MAX_CPU_PERCENT = 75
    , AFFINITY CPU = AUTO
    , MAX_MEMORY_PERCENT = 30
);
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```
  
## <a name="see-also"></a>Voir aussi

+ [external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)
+ [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
+ [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)
+ [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)
+ [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)
+ [Pool de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
+ [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)
+ [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)
+ [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)
