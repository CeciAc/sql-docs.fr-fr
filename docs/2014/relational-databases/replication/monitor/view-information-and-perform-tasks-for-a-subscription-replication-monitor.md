---
title: Afficher des informations et effectuer des tâches pour un abonnement (moniteur de réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subscriptions [SQL Server replication], viewing information
- subscriptions [SQL Server replication], Replication Monitor tasks
- viewing subscription information
ms.assetid: 54aac83b-6f29-40d7-8901-cf059749867f
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: af378e30b8bf33abea688dd9cc36019d18835bed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040388"
---
# <a name="view-information-and-perform-tasks-for-a-subscription-replication-monitor"></a>Afficher des informations et effectuer des tâches relatives à un abonnement (moniteur de réplication)
  Le Moniteur de réplication propose les onglets suivants, qui comportent des informations sur les abonnements :  
  
-   **Tous les abonnements**  
  
     Cet onglet montre des informations sur tous les abonnements à la publication sélectionnée.  
  
-   **Liste de suivi des abonnements**  
  
     Cet onglet est destiné à afficher des informations sur les abonnements de toutes les publications disponibles sur le serveur de publication sélectionné, qui ont des erreurs, des avertissements ou les performances les plus faibles. Cet onglet n'est pas affiché pour les serveurs de distribution exécutant des versions antérieures à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Pour plus d'informations sur les options de chaque onglet, cliquez sur l'onglet dans le volet de droite puis cliquez sur l'option **Aide** dans la barre de menus. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-all-subscriptions-tab"></a>Pour afficher des informations et exécuter des tâches dans l'onglet Tous les abonnements  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Pour afficher des informations sur les abonnements, cliquez sur l'onglet **Tous les abonnements** . Pour n'afficher que les abonnements qui se trouvent dans un état donné, par exemple en cours de synchronisation, sélectionnez une option dans la liste déroulante **Afficher** .  
  
3.  Pour afficher et modifier les propriétés de l'abonnement, cliquez avec le bouton droit sur celui-ci puis cliquez sur **Propriétés**. Vous pouvez également accéder à des informations plus détaillées et effectuer certaines tâches dans cet onglet. Pour plus d’informations, consultez [Afficher des informations et effectuer des tâches pour les agents d’abonnement &#40;moniteur de réplication&#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-subscription-watch-list-tab"></a>Pour afficher des informations et exécuter des tâches dans l'onglet Liste de suivi des abonnements  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Pour consulter des informations sur les abonnements, cliquez sur l'onglet **Liste de suivi des abonnements** .  
  
3.  Sélectionnez le type d’abonnement à afficher dans la liste déroulante **Afficher les abonnements \<Type_abonnement>**. Pour n'afficher que les abonnements qui se trouvent dans un état donné, par exemple en cours de synchronisation, sélectionnez une option dans la liste déroulante **Afficher** .  
  
4.  Pour afficher et modifier les propriétés de l'abonnement, cliquez avec le bouton droit sur celui-ci puis cliquez sur **Propriétés**. Vous pouvez également accéder à des informations plus détaillées et effectuer certaines tâches dans cet onglet. Pour plus d’informations, consultez [Afficher des informations et effectuer des tâches pour les agents d’abonnement &#40;moniteur de réplication&#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un abonnement par émission de données](../view-and-modify-push-subscription-properties.md)   
 [Afficher et modifier les propriétés d’un abonnement par extraction](../view-and-modify-pull-subscription-properties.md)   
 [Surveillance de la réplication](../monitoring-replication.md)  
  
  