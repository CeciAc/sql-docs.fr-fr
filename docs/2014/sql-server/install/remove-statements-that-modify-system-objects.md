---
title: Supprimer les instructions qui modifient les objets système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aca644a822673e4d373048fc0d3a95eb0cd6fdf6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297815"
---
# <a name="remove-statements-that-modify-system-objects"></a>Supprimer les instructions qui modifient les objets système
  Le Conseiller de mise à niveau a détecté des instructions qui mettent à jour le catalogue système. Les mises à jour directes du catalogue système ne sont pas autorisées. Modifiez vos scripts SQL pour utiliser des API officielles et documentées.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les mises à jour directes du catalogue système ne sont pas autorisées. Toute tentative à cet égard génère l'erreur suivante :  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez vos scripts SQL pour utiliser des API officielles et documentées. Par exemple, utilisez ALTER DATABASE *database_name* SET EMERGENCY plutôt que d'exécuter une instruction UPDATE sur la table système **sysdatabases** .  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  