---
title: FilterGroupEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97add08a1d656e8c163600bb0ea8dda7fca264b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932643"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Spécifie le groupe d’enregistrements à filtrer à partir d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Filtres pour afficher uniquement les enregistrements concernés par la dernière [supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) appeler.|  
|**adFilterConflictingRecords**|5\.|Filtres pour afficher les enregistrements qui ont échoué la dernière mise à jour par lots.|  
|**adFilterFetchedRecords**|3|Filtres pour afficher les enregistrements dans le cache actuel-autrement dit, les résultats du dernier appel pour récupérer les enregistrements à partir de la base de données.|  
|**adFilterNone**|0|Supprime le filtre en cours et restaure tous les enregistrements pour l’affichage.|  
|**adFilterPendingRecords**|1|Filtres pour afficher uniquement les enregistrements qui ont été modifiés, mais qui n’ont pas encore été envoyées au serveur. Applicable uniquement pour le mode de mise à jour par lot.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>S'applique à  
 [Filter, propriété](../../../ado/reference/ado-api/filter-property.md)
