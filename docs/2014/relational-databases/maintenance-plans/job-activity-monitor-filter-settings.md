---
title: Moniteur d’activité des travaux (Paramètres du filtre) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d8cdb39e6070e1a7876859d3a620cb852345dbb0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205259"
---
# <a name="job-activity-monitor-filter-settings"></a>Moniteur d'activité des travaux (Paramètres du filtre)
  Cette page vous permet de réduire le nombre de lignes visibles dans le Moniteur d'activité des travaux. Entrez des critères dans une ou plusieurs des zones disponibles, pour afficher uniquement les lignes qui correspondent aux valeurs spécifiées. Certaines zones, telles que **État** ou **Type de blocage** , proposent un nombre défini de valeurs possibles, fournies dans une liste déroulante. D’autres, telles que **Application** , permettent d’entrer n’importe quelle valeur et autant de valeurs que vous le souhaitez, sous la forme d’une liste dont les valeurs sont séparées par une virgule. Les icônes de la barre d'outils vous permettent de trier les zones disponibles par catégorie ou par ordre alphabétique. Cliquez sur des critères pour afficher une brève description de chacun d'eux.  
  
 Pour filtrer le Moniteur d’activité des travaux, fournissez autant de critères de filtre que vous le souhaitez, cliquez sur **Appliquer le filtre**, puis sur **OK**.  
  
## <a name="all-jobs"></a>Tous les travaux  
 Ce groupe de critères de filtre est disponible lors du filtrage du Moniteur d'activité des travaux.  
  
 **Nom**  
 Permet de filtrer les travaux par leur nom.  
  
 **Prochaine exécution**  
 Permet de filtrer par la date de prochaine exécution planifiée.  
  
 **Exécutable**  
 Permet d'afficher les travaux qui peuvent être exécutés ou les travaux qui ne le peuvent pas. Sélectionnez **Oui** pour visualiser uniquement les travaux exécutables, **Non** pour visualiser uniquement les travaux non exécutables ou **Tous** pour visualiser les deux types de travaux.  
  
 **Dernière exécution**  
 Permet de filtrer par la date de dernière exécution.  
  
 **Résultats de la dernière exécution**  
 Permet de filtrer les travaux par l'état de leur dernière exécution.  
  
 **Activé**  
 Permet d'afficher uniquement les travaux activés ou non activés  
  
 **Catégorie**  
 Permet de filtrer les travaux par catégorie.  
  
 **Planifié**  
 Permet d'afficher tous les travaux avec planification ou sans planification.  
  
 **État**  
 Permet de filtrer les travaux par leur état.  
  
## <a name="description-area"></a>Zone Description  
 **Zone de description**  
 Cette zone sans nom fournit une brève description des critères lors de leur sélection.  
  
 **Appliquer le filtre**  
 Pour appliquer le filtre, cliquez sur **Appliquer****le filtre** , puis sur **OK**. Pour conserver les paramètres du filtre dans la boîte de dialogue **Paramètres****du filtre** , sans les appliquer, désactivez l’option **Appliquer****le filtre**, puis cliquez sur **OK**, pour afficher toutes les lignes.  
  
 **Désactiver**  
 Rétablit les paramètres par défaut du filtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller l'activité des travaux](../../ssms/agent/monitor-job-activity.md)  
  
  
