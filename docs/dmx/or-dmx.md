---
title: OR (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 76b1f8ac9a5f7ad584f42110f2c3b22e5c1918ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008142"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un opérateur logique qui effectue une disjonction logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression DMX (Data Mining Extensions) valide qui retourne une valeur numérique.  
  
 *Expression2*  
 Expression DMX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui retourne TRUE si l'un ou l'autre ou les deux arguments donnent comme résultat la valeur TRUE ; dans le cas contraire, elle retourne FALSE.  
  
## <a name="remarks"></a>Notes  
 Les deux arguments sont considérés comme valeurs booléennes (0 correspond à la valeur FALSE ; sinon TRUE) avant que l'opérateur effectue la disjonction logique. Si l'un ou l'autre ou les deux arguments donnent comme résultat la valeur TRUE, l'opérateur retourne TRUE. Si *Expression1* a la valeur TRUE et *Expression2* a la valeur FALSE, l’opérateur retourne TRUE.  
  
 Le tableau ci-dessous explique comment s'effectue la disjonction logique.  
  
|Si Expression1 est|Si Expression2 est|La valeur de retour est|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Opérateurs logiques &#40;DMX&#41;](../dmx/operators-logical.md)   
 [Operators &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
