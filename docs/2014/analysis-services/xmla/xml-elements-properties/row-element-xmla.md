---
title: Élément Row (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- row Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords:
- row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17bc202bb7e1d2c0701b478409b02f4bbb160958
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223989"
---
# <a name="row-element-xmla"></a>Élément row (XMLA)
  Contient une seule ligne de données pour un [racine](root-element-xmla.md) élément qui contient les données sous forme de tableau retournées par une [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) appel de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[racine](root-element-xmla.md) (à l’aide de la [ensemble de lignes](../xml-data-types/rowset-data-type-xmla.md) type de données)|  
|Éléments enfants|Un ou plusieurs éléments de colonne.|  
  
## <a name="remarks"></a>Notes  
 Chaque ligne retournée par un élément `root` contenant des données sous forme de tableau a un élément `row` correspondant. Chaque colonne dans l'élément `root` est représentée par un élément XML distinct. La valeur de la colonne pour l'élément `row` correspond aux données figurant dans l'élément XML, et le nom de la colonne correspond au nom de l'élément XML.  
  
 Il existe deux moyens d'exprimer une valeur NULL pour une colonne au sein d'une ligne :  
  
-   Un élément de colonne manquant implique que la colonne est NULL.  
  
-   L'élément de colonne peut faire appel à l'attribut `xsi:nil='true'` pour indiquer qu'il possède une valeur NULL.  
  
 Par exemple, si une ligne comporte une seule colonne appelée Store_Name, dont la valeur est NULL, elle peut être représentée des deux façons suivantes :  
  
```  
<row>  
</row>  
```  
  
 - ou -  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 Si un élément de colonne contient une erreur, un élément `Error` fournit des informations à propos de cette erreur, comme le décrit l'exemple suivant :  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Pour plus d’informations sur l’appellation de colonne et des informations de schéma pour les données tabulaires, consultez [Type de données Rowset &#40;XMLA&#41;](../xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
