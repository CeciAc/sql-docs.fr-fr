---
title: '! (Non logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 70a95bee2c4d136fbbedfbf5e00afb3724a94c5e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602557"
---
# <a name="-logical-not-ssis-expression"></a>! (Non logique) (expression SSIS)
  Inverse un opérande booléen.  
  
> [!NOTE]  
>  L'opérateur « ! » ne peut pas être utilisé en combinaison avec d'autres opérateurs. Par exemple, vous ne pouvez pas combiner les opérateurs « ! » et > pour former l'opérateur « !> » .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression*  
 Toute expression valide qui s'évalue à une valeur booléenne. Pour plus d'informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 DT_BOOL  
  
## <a name="remarks"></a>Notes   
 Le tableau suivant indique le résultat de l'opération « ! » publication.  
  
|Expression booléenne initiale|Après application de l'opérateur « ! » operator|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L’exemple suivant donne la valeur FALSE si la colonne **Color** a pour valeur « red ».  
  
```  
!(Color == "red")  
```  
  
 L’exemple suivant donne la valeur TRUE si la valeur de la variable **MonthNumber** et celle de l’entier qui représente le mois actuel sont identiques. Pour plus d’informations, consultez [MONTH &#40;expression SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md) et [GETDATE &#40;expression SSIS&#41;](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
