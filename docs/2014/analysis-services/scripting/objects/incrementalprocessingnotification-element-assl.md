---
title: Élément IncrementalProcessingNotification (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IncrementalProcessingNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotification element
ms.assetid: bfc9b0a4-4043-4aaf-82d9-67e7f1d1eb81
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 639d58928b27e965a707602c0ea124c9078e5b47
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120739"
---
# <a name="incrementalprocessingnotification-element-assl"></a>Élément IncrementalProcessingNotification (ASSL)
  Contient des informations pour le [ProactiveCaching](proactivecaching-element-assl.md) élément sur une requête à exécuter pour déterminer la progression du traitement incrémentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[IncrementalProcessingNotification](../data-type/incrementalprocessingnotification-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[IncrementalProcessingNotifications](../collections/incrementalprocessingnotifications-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ProactiveCachingQueryBinding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Élément ProactiveCaching &#40;ASSL&#41;](proactivecaching-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
