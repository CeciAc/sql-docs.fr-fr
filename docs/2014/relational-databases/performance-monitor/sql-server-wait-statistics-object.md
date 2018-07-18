---
title: SQL Server, objet Wait Statistics | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0da9fe7a76acc3cb7e6cb7713c2c498e9683fd26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162720"
---
# <a name="sql-server-wait-statistics-object"></a>SQL Server, objet Wait Statistics
  L'objet de performance **SQLServer:Wait Statistics** contient des compteurs de performances qui créent des rapports d'information sur l'état d'attente.  
  
 Le tableau ci-dessous répertorie les compteurs contenus dans l'objet Wait Statistics.  
  
|Compteurs Statistiques d'attente de SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Attente de verrouillage**|Statistiques des processus attendant un verrou.|  
|**Attente accès tampon journal**|Statistiques des processus attendant qu'un tampon journal soit disponible.|  
|**Attente d'écriture du journal**|Statistiques des processus attendant qu'un tampon journal soit écrit.|  
|**Attente d'allocation de mémoire**|Statistiques des processus attendant qu'une allocation de mémoire devienne disponible.|  
|**Attente d'E/S réseau**|Statistiques concernant l'attente sur l'E/S réseau.|  
|**Attente verrous non spécifiques des pages**|Statistiques concernant les verrous non spécifiques des pages.|  
|**Attente de verrous d'E/S de pages**|Statistiques concernant les verrous d'E/S de pages.|  
|**Attente de verrous de pages**|Statistiques concernant les verrous de pages, qui n'incluent pas les verrous d'E/S.|  
|**Attente d'objets mémoire thread-safe**|Statistiques relatives aux processus en attente d'allocateurs de mémoire thread-safe.|  
|**Attente de propriété de transaction**|Statistiques relatives aux processus de synchronisation d'accès à une transaction.|  
|**Attente du thread de travail**|Statistiques relatives aux processus en attente d'accès à un thread de travail.|  
|**Attente de synchronisation d'espace de travail**|Statistiques relatives aux processus de synchronisation d'accès à un espace de travail.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Description|  
|----------|-----------------|  
|**Temps d'attente moyen (ms)**|Temps moyen pour le type d'attente sélectionné.|  
|**Temps d'attente cumulé (ms) par seconde**|Temps d'attente agrégé par seconde, pour le type d'attente sélectionné.|  
|**Attentes en cours**|Nombre de processus en cours d'attente du type suivant.|  
|**Attentes démarrées par seconde**|Nombre d'attentes démarrées par seconde pour le type d'attente sélectionné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
