---
title: Objet élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Object Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: 99470537-2c4a-4072-9613-940c41c12487
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e4fb7e25b9e813487b612bbd6269c2f080d85f5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178749"
---
# <a name="object-element-xmla"></a>Élément Object (XMLA)
  Contient une référence d'objet utilisée par l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <!-- One or more object identifiers, depending on the parent element -->  
   </Object>  
...  
</Alter>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|Ancêtre ou Parent : [Alter](../xml-elements-commands/create-element-xmla.md) &#124; 0-1 : élément facultatif qui peut se produire une seule fois et une seule fois.<br /><br /> Ancêtre ou Parent : toutes les autres &#124; 1-1 : élément requis qui apparaît une fois et une seule fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ALTER](../xml-elements-commands/alter-element-xmla.md), [sauvegarde](../xml-elements-commands/backup-element-xmla.md), [ClearCache](../xml-elements-commands/clearcache-element-xmla.md), [supprimer](../xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md), [verrou](../xml-elements-commands/lock-element-xmla.md), [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md), [processus](../xml-elements-commands/process-element-xmla.md), [s’abonner](../xml-elements-commands/subscribe-element-xmla.md), [synchroniser](../xml-elements-commands/synchronize-element-xmla.md)|  
|Éléments enfants|Éléments ASSL (Analysis Services Scripting Language) requis. Spécifié en répertoriant les éléments d'ID de l'objet et de ses ancêtres (à l'exclusion de l'objet `Server`.) Par exemple, l'élément `Object` suivant identifie une partition :<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>Notes  
 L'ordre dans lequel les identificateurs apparaissent n'a pas d'importance.  
  
 Pour `Alter` éléments, l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est utilisé en tant que l’objet par défaut si le `Object` élément n’est pas spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
