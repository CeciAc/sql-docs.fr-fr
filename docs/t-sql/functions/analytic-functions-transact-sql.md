---
title: Fonctions analytiques (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 60fbff84-673b-48ea-9254-6ecdad20e7fe
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a850e153a2c64fb3de4828d2698d16cad97d7d17
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38023317"
---
# <a name="analytic-functions-transact-sql"></a>Fonctions analytiques (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

SQL Server prend en charge ces fonctions analytiques :
  
|||  
|-|-|  
|[CUME_DIST &#40;Transact-SQL&#41;](../../t-sql/functions/cume-dist-transact-sql.md)|[LEAD &#40;Transact-SQL&#41;](../../t-sql/functions/lead-transact-sql.md)|  
|[FIRST_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/first-value-transact-sql.md)|[PERCENTILE_CONT &#40;Transact-SQL&#41;](../../t-sql/functions/percentile-cont-transact-sql.md)|  
|[LAG &#40;Transact-SQL&#41;](../../t-sql/functions/lag-transact-sql.md)|[PERCENTILE_DISC &#40;Transact-SQL&#41;](../../t-sql/functions/percentile-disc-transact-sql.md)|  
|[LAST_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/last-value-transact-sql.md)|[PERCENT_RANK &#40;Transact-SQL&#41;](../../t-sql/functions/percent-rank-transact-sql.md)|  
  
Les fonctions analytiques calculent une valeur d’agrégation basée sur un groupe de lignes. Contrairement aux fonctions d’agrégation, les fonctions analytiques peuvent toutefois retourner plusieurs lignes pour chaque groupe. Utilisez des fonctions analytiques pour calculer des moyennes mobiles, des cumuls, des pourcentages ou des résultats de type « N premiers » dans un groupe.
 
## <a name="see-also"></a>Voir aussi
[OVER, clause &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
