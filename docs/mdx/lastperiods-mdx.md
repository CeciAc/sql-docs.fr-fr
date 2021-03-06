---
title: LastPeriods (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6a9337e925da40f148bbe0d2c77fb1cf4f5f1a99
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905782"
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)


  Retourne le jeu des membres antérieurs à et incluant un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Index*  
 Expression numérique valide qui spécifie un nombre de périodes.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si le nombre de périodes spécifié est positif, le **LastPeriods** fonction retourne un jeu de membres qui commencent par le membre qui arrive en dernier *Index* -1 à partir de l’expression de membre spécifié et se termine par le membre spécifié. Le nombre de membres retournés par la fonction est égal à *Index*.  
  
 Si le nombre de périodes spécifié est négatif, le **LastPeriods** fonction retourne un jeu de membres qui commencent par le membre spécifié et se termine par le membre arrivant en premier (- *Index* - 1) à partir du spécifié membre. Le nombre de membres retournés par la fonction est égal à la valeur absolue de *Index*.  
  
 Si le nombre de périodes spécifié est égal à zéro, le **LastPeriods** fonction retourne le jeu vide. Contrairement à la **Lag** (fonction), qui retourne le membre spécifié si 0 est spécifié.  
  
 Si un membre n’est pas spécifié, le **LastPeriods** fonction utilise **Time.CurrentMember**. Si aucune dimension n'est marquée en tant que dimension Time, la fonction analyse et s'exécute sans erreur mais provoque une erreur de cellule dans l'application cliente.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la valeur de mesure par défaut pour les deuxième, troisième et quatrième trimestres de l'année fiscale 2002.  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Cet exemple peut également être écrit à l'aide de l'opérateur « : » (deux-points) :  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 L'exemple suivant retourne la valeur de mesure par défaut du premier trimestre de l'année fiscale 2002. Bien que le nombre de périodes spécifié soit trois, seule une période peut être retournée puisqu'il n'existe aucune période précédente dans l'année fiscale.  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
