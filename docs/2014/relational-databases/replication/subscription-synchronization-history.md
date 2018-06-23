---
title: Abonnement, historique de synchronisation (abonnement de fusion, SQL Server 2005 et versions ultérieur) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.monitor.subscription.synchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: cff5533e7db8ebdc6f8fd2ca03ae5c8aa8059360
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043318"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2005-and-later"></a>Abonnement, Historique de synchronisation (Abonnement de fusion, SQL Server 2005 et version ultérieure)
  L'onglet **Historique de synchronisation** contient des informations détaillées sur l'Agent de fusion, notamment l'état, les statistiques d'articles, l'historique, les messages d'information et les messages d'erreur éventuels.  
  
## <a name="options"></a>Options  
 Sélectionnez les sessions de l'Agent de fusion à afficher dans le menu **Afficher** , puis sélectionnez une session dans la grille **Sessions de l'Agent de fusion**. Les informations détaillées sur cette session figurent dans la grille **Articles traités dans la session sélectionnée**.  
  
 **Afficher**  
 Sélectionnez les sessions de l'Agent de fusion à afficher.  
  
 **État**  
 État de l'Agent de fusion à la fin de la session. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Terminé  
  
-   Nouvel essai  
  
-   Exécution en cours  
  
 **Start Time**  
 Heure d'ouverture de la session.  
  
 **Heure de fin**  
 Heure de fin de la session. Si l'agent ne s'est pas arrêté, ce champ est vide.  
  
 **Duration**  
 Durée d'exécution de l'Agent de fusion au cours d'une session. La durée correspond au délai écoulé si l'Agent est actif ou au délai total si l'Agent a déjà été exécuté.  
  
 **Commandes téléchargées**  
 Nombre de lignes téléchargées en amont au cours de la session de l'Agent de fusion.  
  
 **Commandes téléchargées**  
 Nombre de lignes téléchargées en aval au cours de la session de l'Agent de fusion.  
  
 **Message d'erreur**  
 Si la session s'est terminée par une erreur, ce champ contient le dernier message d'erreur consigné par l'Agent de fusion. Dans le cas contraire, ce champ est vide.  
  
 **Article**  
 Nom de chaque article dans la publication, et phases de traitement suivantes de l'ensemble de la publication :  
  
-   **Initialisation**. Fait référence au démarrage de l'Agent de fusion ; n'est pas identique à l'initialisation d'un abonnement qui implique d'appliquer un instantané.  
  
-   **Modifications de schéma et insertions en bloc**.  
  
-   **Télécharger les modifications vers le serveur de publication**.  
  
-   **Téléchargement des modifications vers l'Abonné**.  
  
 Les phases sont incluses pour que la grille puisse afficher la durée et le pourcentage de temps total correspondant à chaque phase dans la session sélectionnée.  
  
 **% du total**  
 Pourcentage du temps de traitement total correspondant à chaque phase dans la session sélectionnée.  
  
 **Duration**  
 Durée passée dans chaque phase de traitement. La durée correspond au délai écoulé si l'Agent de fusion est en cours d'exécution au cours de la session ou au délai total s'il a déjà été exécuté.  
  
 **Inserts**  
 Nombre de lignes insérées dans cette phase de la session sélectionnée.  
  
 **Mises à jour**  
 Nombre de lignes mises à jour dans cette phase de la session sélectionnée.  
  
 **Suppressions**  
 Nombre de lignes supprimées dans cette phase de la session sélectionnée.  
  
 **Conflits**  
 Nombre de conflits dans la session sélectionnée.  
  
 **Modifications de schéma**  
 Nombre de modifications de schéma dans la session sélectionnée. Ces modifications peuvent résulter : des modifications de schéma répliquées depuis la base de données de publication, de l'ajout ou de la suppression d'articles et de la modification des propriétés d'article ou de publication.  
  
 **Dernier message de la session sélectionnée**  
 Cette zone de texte contient le dernier message dans la session sélectionnée. Si une erreur se produit, elle contient des informations détaillées sur l'erreur et la commande qui a été exécutée lors de l'occurrence de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour les agents associés à un abonnement &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Surveillance de la réplication](monitoring-replication.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  