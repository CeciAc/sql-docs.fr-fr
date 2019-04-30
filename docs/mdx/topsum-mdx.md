---
title: TopSum (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 853390f99f02352fd7814fcec208bba1508c03a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208827"
---
# <a name="topsum-mdx"></a>TopSum (MDX)


  Trie un jeu et retourne les éléments situés le plus en haut, dont le total cumulatif est au moins une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Valeur*  
 Expression numérique valide qui précise la valeur par rapport à laquelle chaque tuple est comparé.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) qui retourne une mesure.  
  
## <a name="remarks"></a>Notes  
 Le **TopSum** fonction calcule la somme d’une mesure spécifique évaluée sur un jeu spécifié, en triant le jeu par ordre décroissant. Elle retourne ensuite les éléments dotés des valeurs les plus élevées dont le total de l'expression numérique spécifiée correspond au moins à la valeur indiquée. Enfin, elle retourne le plus petit sous-ensemble d'un jeu dont le total cumulé est égal au moins à la valeur précisée. Les éléments retournés sont triés du plus grand au plus petit.  
  
> [!IMPORTANT]  
>  Comme le [BottomSum](../mdx/bottomsum-mdx.md) (fonction), le **TopSum** fonction respecte jamais la hiérarchie.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne pour la catégorie Bikes (bicyclettes) le plus petit jeu de membres au niveau City (ville) de la hiérarchie Geography (zone géographique) dans la dimension Geography dont le total cumulé et obtenu à l'aide de la mesure Reseller Sales Amount (volume de vente du revendeur) correspond au moins à la somme de 6 000 000 (en commençant par les membres de jeu en question avec le nombre de ventes le plus important).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
