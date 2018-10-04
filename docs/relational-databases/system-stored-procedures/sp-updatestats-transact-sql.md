---
title: sp_updatestats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 129c7bd5c1932d509b9afc5a28a2548c9fa8c3f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818788"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Exécute la procédure UPDATE STATISTICS sur toutes les tables définies par l'utilisateur et les tables internes de la base de données active.  
  
 Pour plus d’informations sur les statistiques de mise à jour, consultez [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Pour plus d’informations sur les statistiques, consultez [Statistiques](../../relational-databases/statistics/statistics.md).  
    
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="arguments"></a>Arguments  
 [ **@resample** =] **'resample'**  
 Spécifie que **sp_updatestats** utilisera l’option RESAMPLE de le [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) instruction. Si **'resample'** n’est pas spécifié, **sp_updatestats** met à jour des statistiques à l’aide de l’échantillonnage par défaut. **Rééchantillonner** est **varchar(8)** avec une valeur par défaut.  
  
## <a name="remarks"></a>Notes  
 **sp_updatestats** exécute UPDATE STATISTICS, en spécifiant le mot clé ALL sur toutes les tables internes et définies par l’utilisateur dans la base de données. sp_updatestats affiche des messages indiquant sa progression. Une fois la mise à jour terminée, cette procédure signale que les statistiques ont été mises à jour pour toutes les tables.  
  
 sp_updatestats met à jour les statistiques sur les index non cluster désactivés mais ne met pas à jour les statistiques sur les index cluster désactivés.  
  
 Pour les tables sur disque, **sp_updatestats** met à jour des statistiques basées sur le **modification_counter** informations contenues dans le **sys.dm_db_stats_properties** affichage, catalogue mise à jour des statistiques où au moins une ligne a été modifiée. Statistiques sur les tables optimisées en mémoire sont toujours mises à jour lors de l’exécution **sp_updatestats**. Par conséquent, n’exécutez pas **sp_updatestats** plus que nécessaire.  
  
 **sp_updatestats** peut déclencher une recompilation de procédures stockées ou d’autres codes compilés. Toutefois, **sp_updatestats** n’entraînera pas forcément une recompilation, si un seul plan de requête est possible pour les tables référencées et les index sur ces derniers. Une recompilation serait inutile dans ce cas, même si les statistiques sont mises à jour.  
  
 Pour les bases de données avec un niveau de compatibilité inférieur à 90, l’exécution de **sp_updatestats** ne conserve pas le dernier paramètre NORECOMPUTE pour des statistiques spécifiques. Pour les bases de données avec un niveau de compatibilité 90 ou supérieur, sp_updatestats conserve la dernière option NORECOMPUTE pour des statistiques spécifiques. Pour plus d’informations sur la désactivation et la réactivation des mises à jour des statistiques, consultez [Statistiques](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **sysadmin** rôle serveur fixe, ou la propriété de la base de données (**dbo**).  
  
## <a name="examples"></a>Exemples  
 Cet exemple met à jour les statistiques des tables de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Procédures stockées système](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
