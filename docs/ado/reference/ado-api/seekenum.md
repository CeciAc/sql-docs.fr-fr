---
title: SeekEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 886825b4d32354572a5162487add419b00ec35d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931067"
---
# <a name="seekenum"></a>SeekEnum
Spécifie le type de [recherche](../../../ado/reference/ado-api/seek-method.md) à exécuter.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Recherche la première clé égale à *KeyValues*.|  
|**adSeekLastEQ**|2|Recherche la dernière clé égale à *KeyValues*.|  
|**adSeekAfterEQ**|4|Recherche soit une clé égale à *KeyValues* ou juste après l’où cette correspondance.|  
|**adSeekAfter**|8|Recherche une clé où une correspondance avec *KeyValues* serait survenue.|  
|**adSeekBeforeEQ**|16|Recherche soit une clé égale à *KeyValues*ou juste avant l’emplacement qui correspondent.|  
|**adSeekBefore**|32|Recherche une clé juste avant où une correspondance avec *KeyValues* serait survenue.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>S'applique à  
 [Seek, méthode](../../../ado/reference/ado-api/seek-method.md)
