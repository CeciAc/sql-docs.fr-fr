---
title: Opérateurs de comparaison | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31c73e25042df50fba9c1702e7834565c0284fbd
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740898"
---
# <a name="comparison-operators"></a>Opérateurs de comparaison


  Vous utiliser des opérateurs de comparaison avec des données scalaires. Il est possible d'en utiliser dans toute expression MDX (Multidimensional Expressions).  
  
 Pour vérifier une condition, vous pouvez également utiliser des opérateurs de comparaison dans les instructions MDX et les fonctions, telles que l’expression MDX [IIf](../mdx/iif-mdx.md) (fonction). Cependant, si vous utilisez des opérateurs de comparaison pour vérifier une condition, assurez-vous que vous disposez des autorisations appropriées avant de tenter de modifier des données en partant de cette condition. Quiconque ayant accès aux données courantes et pouvant interroger ces données peut utiliser des opérateurs de comparaison pour des requêtes supplémentaires. Cependant, cet accès ne signifie pas que ces personnes disposent ou doivent disposer des autorisations correctes pour modifier les données. En outre, pour préserver l'intégrité des données, limitez le nombre de personnes pouvant interroger et modifier les données.  
  
 Les opérateurs de comparaison sont évalués comme des booléens ; ils retournent la valeur TRUE ou FALSE en fonction du résultat de la condition testée.  
  
 MDX prend en charge les opérateurs de comparaison répertoriés dans le tableau suivant.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[= (Égal à)](../mdx/equal-to-mdx.md)|Pour les arguments non NULL, retourne la valeur TRUE si l'argument de gauche équivaut à l'argument de droite ; sinon, FALSE.<br /><br /> Si un de ces arguments ou les deux donnent comme résultat la valeur NULL, l'opérateur retourne une valeur NULL, à moins que la comparaison `0=null` soit effectuée (dans ce cas, la valeur booléenne contient TRUE).|  
|[<> (Différent de)](../mdx/not-equal-to-mdx.md)|Pour les arguments non NULL, retourne la valeur TRUE si l'argument de gauche n'équivaut pas à l'argument de droite ; sinon, FALSE.<br /><br /> Si un de ces arguments ou les deux donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[> (Supérieur à)](../mdx/greater-than-mdx.md)|Pour les arguments non NULL, retourne la valeur TRUE si l'argument de gauche possède une valeur supérieure à celle de l'argument de droite ; sinon, FALSE.<br /><br /> Si un de ces arguments ou les deux donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[>= (Supérieur ou égal à)](../mdx/greater-than-or-equal-to-mdx.md)|Pour les arguments non NULL, retourne la valeur TRUE si l'argument de gauche possède une valeur supérieure ou égale à celle de l'argument de droite ; sinon, FALSE.<br /><br /> Si un de ces arguments ou les deux donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[< (Inférieur à)](../mdx/less-than-mdx.md)|Pour les arguments non NULL, retourne la valeur TRUE si l'argument de gauche possède une valeur inférieure à celle de l'argument de droite ; sinon, FALSE.<br /><br /> Si un de ces arguments ou les deux donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
|[<= (Inférieur ou égal à)](../mdx/less-than-or-equal-to-mdx.md)|Pour les arguments non NULL, retourne la valeur TRUE si l'argument de gauche possède une valeur inférieure ou égale à celle de l'argument de droite ; sinon, FALSE.<br /><br /> Si un de ces arguments ou les deux donnent comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Opérateurs &#40;syntaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
