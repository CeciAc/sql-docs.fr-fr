---
title: SELECT FROM &lt;modèle&gt;. CONTENU (DMX) | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e00a7f272362a103e94d8cac686201ce79c06322
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842662"
---
# <a name="select-from-ltmodelgtcontent-dmx"></a>SELECT FROM &lt;modèle&gt;. CONTENU (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne l'ensemble de lignes du schéma de modèle d'exploration de données pour le modèle d'exploration de données spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste de colonnes séparées par des virgules, dérivées de l'ensemble de lignes du schéma Content.  
  
 *model*  
 Identificateur du modèle  
  
 *Expression de condition*  
 Facultatif. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Le **SELECT FROM**  *\<modèle > ***. CONTENU** instruction retourne le contenu qui est spécifique à chaque algorithme. Imaginons par exemple que vous souhaitez utiliser les descriptions de toutes les règles d'un modèle de règles d'association dans une application personnalisée. Vous pouvez utiliser un **SELECT FROM \<modèle >. CONTENU** instruction pour retourner des valeurs dans la colonne NODE_RULE du modèle.  
  
 Le tableau suivant répertorie les colonnes incluses dans le contenu du modèle d'exploration de données.  
  
> [!NOTE]  
>  Les algorithmes peuvent interpréter les colonnes différemment afin de représenter le contenu de manière appropriée. Pour obtenir une description du modèle d’exploration de données contenu de chaque algorithme et des conseils sur la façon d’interpréter et d’interroger le contenu de chaque type de modèle du modèle d’exploration de données, consultez [contenu du modèle d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
|Colonne de l'ensemble de lignes CONTENT|Description|  
|---------------------------|-----------------|  
|MODEL_CATALOG|Nom de catalogue. Valeur NULL si le fournisseur ne prend pas en charge les catalogues.|  
|MODEL_SCHEMA|Un nom de schéma non qualifié. Valeur NULL si le fournisseur ne prend pas en charge les schémas.|  
|MODEL_NAME|Nom de modèle. Cette colonne ne peut pas contenir de valeur NULL.|  
|ATTRIBUTE_NAME|Nom de l'attribut qui correspond au nœud.|  
|NODE_NAME|Nom du nœud.|  
|NODE_UNIQUE_NAME|Nom unique du nœud dans le modèle.|  
|NODE_TYPE|Entier qui représente le type du nœud. .|  
|NODE_GUID|GUID du nœud. Valeur NULL en l'absence de GUID.|  
|NODE_CAPTION|Étiquette ou légende associée au nœud. Principalement utilisée à des fins d'affichage. En l'absence de légende, NODE_NAME est retourné.|  
|CHILDREN_CARDINALITY|Nombre d'enfants de ce nœud.|  
|PARENT_UNIQUE_NAME|Nom unique du parent du nœud.|  
|NODE_DESCRIPTION|Description du nœud.|  
|NODE_RULE|Fragment XML qui représente la règle incorporée dans le nœud. Le format de la chaîne XML est basé sur la norme PMML.|  
|MARGINAL_RULE|Fragment XML qui décrit le chemin d'accès du parent vers le nœud.|  
|NODE_PROBABILITY|Probabilité du chemin d'accès qui se termine dans le nœud.|  
|MARGINAL_PROBABILITY|Probabilité d'accès au nœud à partir du nœud parent.|  
|NODE_DISTRIBUTION|Table qui contient des statistiques décrivant la distribution des valeurs dans le nœud.|  
|NODE_SUPPORT|Nombre de cas de support de ce nœud.|  
  
## <a name="examples"></a>Exemples  
 Le code suivant retourne l'ID du nœud parent pour le modèle d'arbre de décision qui a été ajouté à la structure d'exploration de données de publipostage ciblé.  
  
```  
SELECT MODEL_NAME, NODE_NAME FROM [TM Decision Tree].CONTENT  
WHERE NODE_TYPE = 1  
```  
  
 Résultats attendus :  
  
|MODEL_NAME|NODE_NAME|  
|-----------------|----------------|  
|TM_DecisionTree|0|  
  
 La requête suivante utilise le **IsDescendant** fonction pour retourner les enfants immédiats du nœud qui a été retournée dans la requête précédente.  
  
> [!NOTE]  
>  La valeur de NODE_NAME étant une chaîne, vous ne pouvez pas utiliser une instruction de sous-sélection pour retourner la valeur NODE_ID comme argument à la **IsDescendant** (fonction).  
  
```  
SELECT NODE_NAME, NODETYPE, NODE_CAPTION   
FROM [TM Decision Tree].CONTENT  
WHERE ISDESCENDANT('0')  
```  
  
 Résultats attendus :  
  
 S'agissant d'un modèle d'arbre de décision, les descendants du nœud parent du modèle incluent un nœud de statistiques marginales unique, un nœud qui représente l'attribut prédictible et plusieurs nœuds qui contiennent des attributs d'entrée et des valeurs. Pour plus d’informations, consultez [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).  
  
## <a name="using-the-flattened-keyword"></a>Utilisation du mot clé FLATTENED  
 Le contenu du modèle d'exploration de données contient fréquemment des informations intéressantes sur le modèle dans les colonnes de table imbriquée. Le mot clé FLATTENED vous permet de récupérer les données d'une colonne de table imbriquée sans utiliser de fournisseur qui prend en charge les ensembles de lignes hiérarchiques.  
  
 La requête suivante retourne un nœud unique, le nœud de statistiques marginales (NODE_TYPE = 26) d'un modèle Naive Bayes. Cependant, ce nœud contient une table imbriquée dans la colonne NODE_DISTRIBUTION. En conséquence, la colonne de table imbriquée est aplatie et une ligne est retournée pour chaque ligne de la table imbriquée. La valeur de la colonne scalaire MODEL_NAME est répétée pour chaque ligne de la table imbriquée.  
  
 Notez par ailleurs que si vous spécifiez uniquement le nom de la colonne de table imbriquée, une nouvelle colonne est retournée pour chaque colonne de la table. Par défaut, le nom de la table imbriquée est ajouté en préfixe au nom de chaque colonne de table.  
  
```  
SELECT FLATTENED MODEL_NAME, NODE_DISTRIBUTION  
FROM [TM_NaiveBayes].CONTENT  
WHERE NODE_TYPE = 26  
```  
  
 Résultats de l'exemple :  
  
|MODEL_NAME|NODE_DISTRIBUTION.ATTRIBUTE_NAME|NODE_DISTRIBUTION.ATTRIBUTE_VALUE|NODE_DISTRIBUTION.SUPPORT|NODE_DISTRIBUTION.PROBABILITY|NODE_DISTRIBUTION.VARIANCE|NODE_DISTRIBUTION.VALUETYPE|  
|-----------------|----------------------------------------|-----------------------------------------|--------------------------------|------------------------------------|---------------------------------|----------------------------------|  
|TM_NaiveBayes|Bike Buyer|Manquant|0|0|0| 1|  
|TM_NaiveBayes|Bike Buyer|0|6556|0.506685215240745|0||  
|TM_NaiveBayes|Bike Buyer| 1|6383|0.493314784759255|0||  
  
 L'exemple suivant montre comment retourner uniquement certaines des colonnes de la table imbriquée en utilisant une instruction sub-select. Vous pouvez simplifier l'affichage en utilisant un alias pour le nom de la table imbriquée, tel qu'indiqué.  
  
```  
SELECT MODEL_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT] AS t  
FROM NODE_DISTRIBUTION)   
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
 Résultats de l'exemple :  
  
|MODEL_NAME|t.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|  
|-----------------|-----------------------|------------------------|---------------|  
|TM_NaiveBayes|Bike Buyer|Manquant|0|  
|TM_NaiveBayes|Bike Buyer|0|6556|  
|TM_NaiveBayes|Bike Buyer| 1|6383|  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
