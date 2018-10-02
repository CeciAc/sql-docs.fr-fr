---
title: Broker, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8f62304b466f5de4716b702f014e39dc72b759b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856137"
---
# <a name="broker-event-category"></a>Catégorie d'événement Broker
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La catégorie d’événement **Broker** contient des événements généraux de Service Broker.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événement Broker:Activation](../../relational-databases/event-classes/broker-activation-event-class.md)|Événement généré lorsqu'un moniteur de file d'attente démarre une procédure stockée d'activation.|  
|[Classe d'événement Broker:Connection](../../relational-databases/event-classes/broker-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport gérée par Service Broker.|  
|[Classe d'événements Broker:Conversation](../../relational-databases/event-classes/broker-conversation-event-class.md)|Événement généré pour rapporter les progrès d'une conversation.|  
|[Classe d'événement Broker:Conversation Group](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|Événement généré lorsque la base de données crée ou supprime un groupe de conversations.|  
|[Classe d'événements Broker:Corrupted Message](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|Événement généré pour indiquer que la base de données a reçu un message endommagé.|  
|[Classe d'événements Broker:Forwarded Message Dropped](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|Événement généré lorsque SQL Server supprime un message Service Broker qui aurait dû être transféré.|  
|[Broker:Forwarded Message Sent (classe d'événements)](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|Événement généré lorsque SQL Server transfère un message Service Broker.|  
|[Classe d'événements Broker:Message Classify](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Événement généré lorsque Service Broker détermine le routage d'un message.|  
|[Classe d'événements Broker:Message Drop](../../relational-databases/event-classes/broker-message-drop-event-class.md)|Événement généré lorsque Service Broker ne peut pas conserver un message reçu qui aurait dû être remis à un service dans cette instance.|  
|[Classe d'événements Broker:Remote Message Ack](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Événement généré lorsque Service Broker envoie ou reçoit un accusé de réception du message.|  
  
 Deux événements d'audit de sécurité sont également fournis pour Service Broker. Pour plus d’informations sur ces événements, consultez [Classe d’événements Audit Broker Login](../../relational-databases/event-classes/audit-broker-login-event-class.md) et [Classe d’événement Audit Broker Conversation](../../relational-databases/event-classes/audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Catégorie d'événement Audit de sécurité](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
