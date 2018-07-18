---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ea29b3ef2bc08e3451f402f17bed298b982f1bc2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407548"
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7901|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Texte du message|L’instruction de réparation n’a pas été traitée. Ce niveau de réparation n'est pas pris en charge lorsque la base de données est en mode d'urgence.|  
  
## <a name="explanation"></a>Explication  
 La base de données est en mode d'urgence et un niveau de réparation autre que REPAIR_ALLOW_DATA_LOSS a été spécifié. Les réparations ne peuvent pas être effectuées en mode d'urgence si REPAIR_ALLOW_DATA_LOSS n'est pas spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez de nouveau la commande et spécifiez l'option REPAIR_ALLOW_DATA_LOSS.  
  
  
