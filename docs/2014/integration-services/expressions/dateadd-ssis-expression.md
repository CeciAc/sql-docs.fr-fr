---
title: DATEADD (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c744d3f28bc27373f3dc9798ba591848d4b720e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62769346"
---
# <a name="dateadd-ssis-expression"></a>DATEADD (expression SSIS)
  Renvoie une nouvelle valeur DT_DBTIMESTAMP après l'ajout d'un nombre qui représente un intervalle de date ou d'heure à la partie de date spécifiée d'une date. Le paramètre numérique doit s'évaluer à un entier et le paramètre de date doit s'évaluer à une date valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a>Arguments  
 *datepart*  
 Paramètre spécifiant la partie de la date à laquelle ajouter un nombre.  
  
 *nombre*  
 Valeur utilisée pour incrémenter *datepart*. La valeur doit être une valeur entière connue au moment de l'analyse de l'expression.  
  
 *date*  
 Expression renvoyant une date valide ou une chaîne dans un format de date.  
  
## <a name="result-types"></a>Types de résultats  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant décrit les parties de date et les abréviations reconnues par l'évaluateur d'expression. Les noms de partie de date ne respectent pas la casse.  
  
|partie de date|Abréviations|  
|--------------|-------------------|  
|Année|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Jour de l'année|dy, y|  
|Jour|dd, d|  
|Week|wk, ww|  
|JourSem|dw, w|  
|Heure|Hh|  
|Minute|mi, n|  
|Seconde|ss, s|  
|Milliseconde|Ms|  
  
 L’argument *nombre* doit être disponible quand l’expression est analysée. Cet argument peut être une constante ou une variable. Vous ne pouvez pas utiliser des valeurs de colonne car celles-ci ne sont pas connues lorsque l'expression est analysée.  
  
 L’argument *datepart* doit être placé entre guillemets.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 La fonction DATEADD renvoie un résultat NULL si l'argument est NULL.  
  
 Des erreurs se produisent dans les cas suivants : une date n'est pas valide, l'unité de date ou d'heure n'est pas une chaîne ou l'incrément n'est pas un entier statique.  
  
## <a name="ssis-expression-examples"></a>Exemples d'expressions SSIS  
 L'exemple suivant ajoute un mois à la date actuelle.  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 L’exemple suivant ajoute 21 jours aux dates de la colonne **ModifiedDate** .  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 L'exemple suivant ajoute 2 années à une date littérale.  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEDIFF &#40;expression SSIS&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](datepart-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](day-ssis-expression.md)   
 [MONTH &#40;expression SSIS&#41;](month-ssis-expression.md)   
 [YEAR &#40;expression SSIS&#41;](year-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
