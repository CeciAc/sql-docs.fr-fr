---
title: Accès à un enregistrement | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record jumping [ADO]
- jumping to record [ADO]
ms.assetid: 6caf6299-2eea-4d34-9b0e-b75aab07b740
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cefa6ac39d68040106d38e5f1cfbec8a6eff8358
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700692"
---
# <a name="jumping-to-a-record"></a>Accès à un enregistrement
Le [déplacer](../../../ado/reference/ado-api/move-method-ado.md) méthode vous permet de faire avancer ou reculer dans le **Recordset** un nombre spécifié d’enregistrements à l’aide de la syntaxe suivante :  
  
```  
oRs.Move NumRecords, Start  
```  
  
## <a name="remarks"></a>Notes  
 Le **déplacer** méthode est prise en charge sur tous les **Recordset** objets.  
  
 Si le *NbEnregistrements* argument est supérieur à zéro, la position actuelle se déplace vers l’avant (vers la fin de la **Recordset**). Si *NbEnregistrements* est inférieur à zéro, la position actuelle se déplace vers l’arrière (vers le début de la **Recordset**).  
  
 Si le **déplacer** appel serait déplace la position actuelle vers un point situé avant le premier enregistrement, ADO définit l’enregistrement actif à la position avant le premier enregistrement dans le **Recordset** (**BOF** est **True**). Une tentative de déplacement vers l’arrière quand le **BOF** propriété est déjà **True** génère une erreur.  
  
 Si le **déplacer** appel déplacerait la position actuelle vers un point après le dernier enregistrement, ADO définit l’enregistrement actif à la position après le dernier enregistrement dans le **Recordset** (**EOF** est **True**). Une tentative de déplacement vers l’avant quand le **EOF** propriété est déjà **True** génère une erreur.  
  
 Appel de la **déplacer** méthode à partir de vide **Recordset** objet génère une erreur.  
  
 Si vous passez un signet dans le *Démarrer* argument, le déplacement est relatif à l’enregistrement avec ce signet, en supposant que le **Recordset** objet prend en charge les signets. Un signet est obtenu en utilisant la [signet](../../../ado/reference/ado-api/bookmark-property-ado.md) propriété. Si non spécifié, le déplacement est relatif à l’enregistrement actif.  
  
 Si vous utilisez le **CacheSize** propriété à mettre en cache localement les enregistrements à partir du fournisseur, en passant un *NbEnregistrements* argument qui déplace la position actuelle en dehors du groupe actuel d’enregistrements mis en cache force ADO à récupérer un nouveau groupe d’enregistrements, à partir de l’enregistrement de destination. Le **CacheSize** propriété détermine la taille du groupe qui vient d’être extrait et l’enregistrement de destination est le premier enregistrement récupéré.
