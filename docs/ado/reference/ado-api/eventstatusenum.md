---
title: Il ne | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20a5582eb8c8744e5d8a065c5fa8ce29c0d4b793
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278058"
---
# <a name="eventstatusenum"></a>Il n'
Spécifie l’état actuel de l’exécution d’un événement.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adStatusCancel**|4|Demande l’annulation de l’opération qui a provoqué l’événement se produit.|  
|**adStatusCantDeny**|3|Indique que l’opération ne peut pas demander l’annulation de l’opération en attente.|  
|**adStatusErrorsOccurred**|2|Indique que l’opération qui a provoqué l’événement a échoué en raison d’une erreur ou des erreurs.|  
|**adStatusOK**| 1|Indique que l’opération qui a provoqué l’événement a réussi.|  
|**adStatusUnwantedEvent**|5|Empêche toute notification avant que la méthode d’événement ait terminé l’exécution.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.EventStatus.CANCEL|  
|AdoEnums.EventStatus.CANTDENY|  
|AdoEnums.EventStatus.ERRORSOCCURRED|  
|AdoEnums.EventStatus.OK|  
|AdoEnums.EventStatus.UNWANTEDEVENT|  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[BeginTransComplete, CommitTransComplete et RollbackTransComplete, événements (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[ConnectComplete et Disconnect, événements (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[EndOfRecordset, événement (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[ExecuteComplete, événement (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[FetchComplete, événement (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[InfoMessage, événement (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[WillChangeField et FieldChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[WillChangeRecord et RecordChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset et RecordsetChangeComplete, événements (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillConnect, événement (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[WillExecute, événement (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[WillMove et MoveComplete, événements (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
