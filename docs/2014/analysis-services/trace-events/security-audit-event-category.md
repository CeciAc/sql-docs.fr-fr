---
title: Catégorie d’événement d’Audit de sécurité | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 00b609451a5513e801acf41f4f0ac87ae0a932b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041681"
---
# <a name="security-audit-event-category"></a>Catégorie d'événement Audit de sécurité
  La catégorie d'événement Audit de sécurité contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Audit Login| 1|Enregistre tous les événements de connexion depuis le début de la trace, tels qu’une demande de connexion d’un client à un serveur qui exécute une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Audit Logout|2|Enregistre tous les nouveaux événements de déconnexion depuis le début de la trace, tels que l'émission par un client d'une commande de déconnexion.|  
|Audit Server Starts And Stops|4|Enregistre l'arrêt, le début et la suspension des activités des services.|  
|Audit Object Permission Event|18|Enregistre toutes les modifications d'autorisations sur les objets.|  
|Audit Admin Operations Event|19|Enregistre des opérations de serveur pour la sauvegarde, la restauration, la synchronisation, l'attachement, le détachement, ainsi que pour le chargement et la sauvegarde d'images.|  
  
 Pour plus d’informations sur les colonnes associées à chaque classe d’événements Security Audit, consultez [Colonnes de données Audit de sécurité](security-audit-data-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de Trace Analysis Services](analysis-services-trace-events.md)  
  
  