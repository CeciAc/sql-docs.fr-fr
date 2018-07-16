---
title: Détecter et résoudre les conflits de réplication de fusion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6fff24c04e3fc434f6ebf41549cfe78682ca1805
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260505"
---
# <a name="detect-and-resolve-merge-replication-conflicts"></a>Détecter et résoudre de conflits de réplication de fusion
  Lorsqu'un serveur de publication et un Abonné sont connectés et que la synchronisation se produit, l'Agent de fusion détecte la présence d'éventuels conflits. Si tel est le cas, l'Agent de fusion utilise un programme de résolution de conflits pour déterminer les données qui doivent être acceptées et propagées aux autres sites.  
  
> [!NOTE]  
>  Bien qu'un Abonné se synchronise avec le serveur de publication, les conflits se produisent généralement entre les mises à jour des différents Abonnés plutôt qu'entre les mises à jour de l'Abonné et du serveur de publication.  
  
 La réplication de fusion propose plusieurs méthodes de détection et de résolution des conflits. Pour la plupart des applications, la méthode par défaut est la plus adaptée :  
  
-   Si un conflit se produit entre un serveur de publication et un Abonné, la modification du serveur de publication est conservée tandis que celle de l'Abonné est annulée.  
  
-   Si un conflit se produit entre deux Abonnés utilisant des abonnements client (le type par défaut des abonnements par extraction de données), la modification provenant du premier Abonné pour se synchroniser avec le serveur de publication est conservée tandis que celle provenant du second Abonné est annulée. Pour plus d’informations sur la spécification des abonnements client et serveur, consultez [Spécifier un type d’abonnement de fusion et une priorité pour la résolution des conflits &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
-   Si un conflit se produit entre deux Abonnés utilisant des abonnements serveur (le type par défaut des abonnements par envoi de données), la modification provenant de l'Abonné ayant la valeur de priorité la plus élevée est conservée tandis que celle provenant du second Abonné est annulée. Si les valeurs de priorité sont identiques, la modification provenant du premier Abonné pour se synchroniser avec le serveur de publication est conservée.  
  
 Pour plus d'informations sur la détection et la résolution des conflits pour la réplication de fusion, consultez [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Options d’articles pour la réplication de fusion](article-options-for-merge-replication.md)   
 [S’abonner à des publications](../subscribe-to-publications.md)  
  
  
