---
title: Trier des colonnes | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 39914adea566ef938b4f33a771ecba0a8f4caf95
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287136"
---
# <a name="sort-columns"></a>Trier les colonnes
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  La boîte de dialogue **Trier les colonnes** vous permet de trier des grilles dans le Moniteur de réplication selon une ou plusieurs colonnes (vous pouvez également effectuer un tri sur une colonne unique en cliquant sur l'en-tête de colonne dans la grille du Moniteur de réplication). Par exemple, pour trier des abonnements sous l'onglet **Tous les abonnements** selon l'état, puis selon le type de connexion, procédez comme suit :  
  
1.  Dans la première ligne de la grille, sélectionnez **État** dans la colonne **Nom de la colonne** et une valeur dans la colonne **Ordre de tri** .  
  
2.  Dans la deuxième ligne de la grille, sélectionnez **Type de connexion** dans la colonne **Nom de la colonne** et une valeur dans la colonne **Ordre de tri** .  

## <a name="options"></a>Options  
 **Nom de la colonne**  
 Nom de la colonne sur laquelle vous souhaitez effectuer le tri. Vous pouvez effectuer le tri sur une ou plusieurs colonnes. Vous ne pouvez pas trier sur les colonnes **Performance moyenne actuelle** ou **Pire performance actuelle** sous l'onglet **Publications** en raison de la façon dont ces valeurs de colonne sont calculées.  
  
 **Ordre de tri**  
 Spécifiez **Croissant** ou **Décroissant**.  
  
 **Effacer tout**  
 Supprime toutes les lignes de la grille de tri. Pour supprimer une ligne unique, sélectionnez la ligne et appuyez sur la touche Suppr.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
