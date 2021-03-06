---
title: Les curseurs dynamiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86e51b7880004117e8efc96bd310c6de705d43a6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925508"
---
# <a name="dynamic-cursors"></a>Curseurs dynamiques
Les curseurs dynamiques détectent toutes les modifications apportées aux lignes du jeu de résultats, indépendamment de si les modifications se produisent à partir de l’intérieur du curseur ou par d’autres utilisateurs en dehors du curseur. Tous les insert, update et les instructions delete effectuées par tous les utilisateurs sont visibles à travers le curseur. Le curseur dynamique peut détecter les modifications apportées aux lignes, de commande et de valeurs dans le jeu de résultats après l’ouverture du curseur. Mises à jour effectuées en dehors du curseur ne sont pas visibles jusqu'à ce qu’elles sont validées (sauf si le niveau d’isolation de transactions de curseur est défini « non validé »).  
  
 Par exemple, un curseur dynamique extrait deux lignes et une autre application, puis met à jour un de ces lignes et supprime l’autre. Si le curseur dynamique extrait alors ces lignes, il ne trouvera pas la ligne supprimée, mais il affichera les nouvelles valeurs pour la ligne mise à jour.  
  
 Le curseur dynamique est un bon choix si votre application doit détecter toutes les mises à jour simultanées apportées par d’autres utilisateurs. Utiliser le **adOpenDynamic CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur dynamique dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs statiques](../../../ado/guide/data/static-cursors.md)   
 [Curseurs de jeu de clés](../../../ado/guide/data/keyset-cursors.md)
