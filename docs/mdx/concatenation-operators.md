---
title: Opérateurs de concaténation | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7298f80a7d3f61b5b00692be8fbc480429487454
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892459"
---
# <a name="concatenation-operators"></a>Opérateurs de concaténation


  L'opérateur de concaténation est le signe plus (+). Vous pouvez combiner, ou concaténer, deux ou plusieurs chaînes de caractères en une seule. Vous pouvez également concaténer des chaînes binaires.  
  
 Le code suivant est un exemple d'opérateur de concaténation combinant le nom du produit et son nom unique :  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>Observations relatives au langage  
 Lorsque les chaînes utilisées dans une concaténation possèdent toutes deux le même classement, la chaîne concaténée obtenue possède un classement identique aux entrées. Lorsque les chaînes utilisées dans une concaténation possèdent des classements différents, les règles de priorité de classement déterminent celui de la chaîne concaténée obtenue. Pour plus d’informations, consultez [Langues et classements &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/languages-and-collations-analysis-services).  
  
## <a name="see-also"></a>Voir aussi  
 [MDX de référence &#40;des opérateurs MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Syntaxe &#40;MDX des opérateurs&#41;](../mdx/operators-mdx-syntax.md)  
  
  
