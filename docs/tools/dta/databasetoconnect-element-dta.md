---
title: Databasetoconnect, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e1a8ccb53f30f71abf58480cebc261fe5ff68658
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733425"
---
# <a name="databasetoconnect-element-dta"></a>DatabaseToConnect, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Spécifie la première base de données à laquelle l'Assistant Paramétrage du moteur de base de données se connecte lors du paramétrage d'une charge de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Peut être utilisé une seule fois pour chaque élément **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Éléments enfants**|None|  
  
## <a name="remarks"></a>Notes  
 Utilisez **DatabaseToConnect** pour spécifier le nom de la première base de données à laquelle vous souhaitez que l'Assistant Paramétrage du moteur de base de données se connecte lorsqu'il démarre une session de paramétrage. Vous ne pouvez spécifier qu'une seule base de données avec cet élément. Si plusieurs noms de bases de données sont spécifiées, l'Assistant Paramétrage du moteur de base de données renvoie une erreur.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez [Exemple de fichier d’entrée XML avec une charge de travail Inline &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
