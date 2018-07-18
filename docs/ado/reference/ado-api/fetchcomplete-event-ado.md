---
title: FetchComplete, événement (ADO) | Documents Microsoft
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
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6d8024a302d76ad01aa3044c675fc2a42c7c7ed
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278148"
---
# <a name="fetchcomplete-event-ado"></a>FetchComplete, événement (ADO)
Le **FetchComplete** événement est appelé une fois que tous les enregistrements dans une opération asynchrone de longue durée ont été récupérés dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Elle décrit l’erreur qui s’est produite si la valeur de **ne** est **contraire**; sinon, elle n’est pas définie.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état. Lorsque cet événement est appelé, ce paramètre est défini **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou pour **contraire** si l’opération a échoué.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *pRecordset*  
 A **Recordset** objet. L’objet pour lequel les enregistrements ont été récupérés.  
  
## <a name="remarks"></a>Notes  
 Pour utiliser **FetchComplete** avec Microsoft Visual Basic, Visual Basic 6.0 ou version ultérieure est requis.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
