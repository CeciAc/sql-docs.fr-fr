---
title: Définition et identification d’objets (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad6c8de47577eccd7797517c8080957d7afe1abd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62727542"
---
# <a name="defining-and-identifying-objects-xmla"></a>Définition et identification d'objets (XMLA)
  Les objets sont identifiés dans les commandes XMLA (XML for Analysis) à l'aide d'identificateurs et de références d'objet, et ils sont définis à l'aide de commandes XMLA contenant des éléments ASSL (Analysis Services Scripting Language).  
  
## <a name="object-identifiers"></a>Identificateurs d'objet  
 Un objet est identifié à l’aide de l’identificateur unique de l’objet tel que défini sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les identificateurs d'objet peuvent être spécifiés explicitement ou déterminés par l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] au moment où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée l'objet. Vous pouvez utiliser la [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) méthode pour récupérer les identificateurs d’objet pour suivantes `Discover` ou [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) appels de méthode.  
  
## <a name="object-references"></a>Références d'objet  
 Plusieurs commandes XMLA, tel que [supprimer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) ou [processus](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), utilisez une référence d’objet pour faire référence à un objet de façon non équivoque. Une référence d'objet contient l'identificateur de l'objet sur lequel une commande est exécutée, ainsi que les identificateurs des ancêtres de cet objet. Par exemple, dans le cas d'une partition, la référence d'objet contient l'identificateur d'objet de la partition, ainsi que les identificateurs d'objet du groupe de mesures parent, du cube et de la base de données de cette partition.  
  
## <a name="object-definitions"></a>Définition d'objets  
 Le [créer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) et [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) commandes XMLA créer ou modifier, respectivement, objets sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance. Les définitions de ces objets sont représentées par une [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) élément qui contient les éléments ASSL. Identificateurs d’objet peuvent être spécifiés explicitement pour les principaux et de nombreux objets secondaires à l’aide de la [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) élément. Si l'élément `ID` n'est pas utilisé, l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit un identificateur unique, avec une convention d'affectation des noms qui dépend de l'objet à identifier. Pour plus d’informations sur l’utilisation de la `Create` et `Alter` commandes pour définir des objets, consultez [création et modification des objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément objet &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Élément ParentObject &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Élément source &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Élément Target &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
