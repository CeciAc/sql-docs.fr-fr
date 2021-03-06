---
title: Prédire (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb939c45d298117fa81b05d6188aa3a4c5cd7c4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008157"
---
# <a name="predict-dmx"></a>Predict (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Le **Predict** fonction retourne une valeur prédite, ou un ensemble de valeurs, pour une colonne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Référence de colonne scalaire ou référence de colonne de table.  
  
## <a name="return-type"></a>Type de retour  
 \<référence de colonne scalaire >  
  
 ou Gestionnaire de configuration  
  
 \<référence de colonne de table >  
  
 Le type de retour dépend du type de colonne auquel cette fonction est appliquée.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY et INCLUDE_STATISTICS s'appliquent uniquement à une référence de colonne de table, et EXCLUDE_NULL et INCLUDE_NULL s'appliquent uniquement à une référence de colonne scalaire.  
  
## <a name="remarks"></a>Notes  
 Les options sont EXCLUDE_NULL (par défaut), INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (par défaut), INPUT_ONLY et INCLUDE_STATISTICS.  
  
> [!NOTE]  
>  Pour les modèles de série chronologique, la fonction Predict ne prend pas en charge INCLUDE_STATISTICS.  
  
 Le paramètre INCLUDE_NODE_ID retourne la colonne $NODEID dans le résultat. NODE_ID est le nœud de contenu sur lequel la prédiction est exécutée pour un cas particulier. Ce paramètre est facultatif lors de l’utilisation de Predict sur les colonnes de table.  
  
 Le *n* paramètre s’applique aux colonnes de table. Il définit le nombre de lignes retournées en fonction du type de prédiction. Si la colonne sous-jacente est la séquence, il appelle le **PredictSequence** (fonction). Si la colonne sous-jacente est de série chronologique, il appelle le **PredictTimeSeries** (fonction). Pour les types de prédictions associatives, il appelle le **PredictAssociation** (fonction).  
  
 Le **Predict** fonction prend en charge le polymorphisme.  
  
 Les formes abrégées des autres solutions suivantes sont fréquemment utilisées :  
  
-   [Gender] est une alternative pour **Predict**([Gender], EXCLUDE_NULL).  
  
-   [Products Purchases] est une alternative pour **Predict**([Products Purchases], EXCLUDE_NULL, EXCLUSIVE).  
  
    > [!NOTE]  
    >  Le type de retour de cette fonction est lui-même considéré comme une référence de colonne. Cela signifie que le **Predict** fonction peut être utilisée en tant qu’argument dans d’autres fonctions qui acceptent une référence de colonne en tant qu’argument (à l’exception de la **Predict** fonction elle-même).  
  
 En passant INCLUDE_STATISTICS à une prédiction sur une colonne de table-valued ajoute les colonnes **$Probability** et **$Support** à la table résultante. Ces colonnes décrivent la probabilité de l'existence de l'enregistrement de table imbriquée associée.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la fonction Predict pour retourner les quatre produits dans la base de données Adventure Works qui sont susceptibles d’être vendus ensemble. Étant donné que la fonction est la prédiction par rapport aux règles association modèle d’exploration de données, il utilise automatiquement le **PredictAssociation** fonctionne comme décrit précédemment.  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 Exemples de résultats :  
  
 Cette requête retourne une ligne de données unique à une colonne (`Expression`) qui contient la table imbriquée suivante.  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Water Bottle|2866|0.192620471805901|0.175205052318795|  
|Patch Kit|2113|0.142012232004839|0.132389356196586|  
|Mountain Tire Tube|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
