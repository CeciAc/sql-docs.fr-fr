---
title: Catégorie d’événements de traitement des requêtes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a94b3198-be85-4935-845d-1cd4e121fc94
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ee6ef696f26397c3b4ca7656710d666d6e1941d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261485"
---
# <a name="query-processing-events-category"></a>Catégorie d'événements de traitement de requête
  La catégorie d'événement Query Processing contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|**Classe d'événements**|**ID d'événement**|**Description**|  
|---------------------|------------------|---------------------|  
|Query Subcube|11|Requête sur un sous-cube, pour une optimisation basée sur l'utilisation.|  
|Query Subcube Verbose|12|Requête sur un sous-cube avec des informations détaillées. Cet événement peut avoir un impact négatif sur la performance en cas d'activation.|  
|Get Data From Aggregation|60|Répondre à la requête en obtenant des données à partir de l'agrégation. Cet événement peut avoir un impact négatif sur la performance en cas d'activation.|  
|Get Data From Cache|61|Répondre à la requête en obtenant des données à partir de l'un des caches. Cet événement peut avoir un impact négatif sur la performance en cas d'activation.|  
|Query Cube Begin|70|Collecte tous les événements Query Cube Begin depuis le début de la trace.|  
|Query Cube End|71|Collecte tous les événements Query Cube End depuis le début de la trace.|  
|Calculate Non Empty Begin|72|Calculer non vide Début.|  
|Calculate Non Empty Current|73|Calculer non vide En cours.|  
|Calculate Non Empty End|74|Calculer non vide Fin.|  
|Serialize Results Begin|75|Sérialiser résultats Début.|  
|Serialize Results Current|76|Sérialiser résultats En cours.|  
|Serialize Results End|77|Sérialiser résultats Fin.|  
|Execute MDX Script Begin|78|Exécuter script MDX Début.|  
|Execute MDX Script Current|79|Exécuter script MDX En cours.|  
|Execute MDX Script End|80|Exécuter script MDX Fin.|  
|Query Dimension|81|Dimension de requête.|  
|VertiPaq SE Query Begin|82|Requête VertiPaq SE|  
|VertiPaq SE Query End|83|Requête VertiPaq SE|  
  
 Pour plus d'informations sur les colonnes associées à chaque classe d'événements Query Processing, consultez [Query Processing Events Data Columns](query-processing-events-data-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de trace Analysis Services](analysis-services-trace-events.md)  
  
  
