---
title: Diviser (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: af4f0f53a1822d2fd45fdbaacfd9ab05d783c237
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62769326"
---
# <a name="divide-ssis-expression"></a>Diviser (expression SSIS)
  Divise la première expression numérique par la deuxième.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Arguments  
 *dividend*  
 Expression numérique à diviser. *dividend* peut être n’importe quelle expression numérique valide. Pour plus d’informations, consultez [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Expression numérique par laquelle diviser le dividende. *divisor* peut être n’importe quelle expression numérique valide, sauf zéro.  
  
## <a name="result-types"></a>Types de résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
 La division par zéro n'est pas autorisée. L’évaluation de la sous-expression *divisor* génère l’une des erreurs suivantes :  
  
-   Si la sous-expression *divisor* qui donne la valeur zéro est une constante, l’erreur se produit au moment de la conception et provoque l’échec de la validation de l’expression.  
  
-   Si la sous-expression *divisor* qui donne la valeur zéro contient des variables, mais aucune colonne d’entrée, le composant auquel l’expression appartient ne parvient pas à valider l’exécution préalable du package.  
  
-   Si la sous-expression *divisor* qui donne la valeur zéro contient des colonnes d’entrée, l’erreur se produit au moment de l’exécution et est gérée en fonction des règles de flux d’erreur du composant de flux de données.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant divise deux littéraux numériques.  
  
```  
25 / 5  
```  
  
 L’exemple suivant divise les valeurs de la colonne **ListPrice** par celles de la colonne **StandardCost** .  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
