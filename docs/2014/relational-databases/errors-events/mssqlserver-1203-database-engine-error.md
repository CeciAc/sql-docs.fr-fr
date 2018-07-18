---
title: MSSQLSERVER_1203 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3685f5ab9eb498c00c1837f19e55cf6f721f5a3f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410688"
---
# <a name="mssqlserver1203"></a>MSSQLSERVER_1203
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1203|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LK_NOT|  
|Texte du message|L'ID de processus %d a essayé de déverrouiller une ressource qu'il ne possède pas :%.*ls. Réessayez la transaction, car cette erreur est peut-être provoquée par une condition basée sur le temps. Si le problème persiste, contactez l'administrateur de base de données.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est engagé dans une activité autre que le nettoyage de post-traitement standard et que la page qu'il est en train d'essayer de déverrouiller est déjà déverrouillée.  
  
### <a name="possible-causes"></a>Causes possibles  
 La cause sous-jacente de cette erreur peut être liée à des problèmes structurels au sein de la base de données concernée. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère l'acquisition et la libération de pages pour maintenir le contrôle de simultanéité dans l'environnement multi-utilisateur. Ce mécanisme est géré à l'aide de diverses structures de verrous internes qui identifient la page et le type de verrou présent. Les verrous sont acquis pour le traitement des pages concernées, puis libérés une fois le traitement terminé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez DBCC CHECKDB sur la base de données à laquelle appartient l'objet. Si DBCC CHECKDB n'indique aucune erreur, essayez de rétablir la connexion et d'exécuter la commande.  
  
> [!IMPORTANT]  
>  Si l'exécution de DBCC CHECKDB avec l'une des clauses REPAIR ne résout pas le problème d'index ou si vous ne savez pas quelles conséquences l'exécution de DBCC CHECKDB avec une clause REPAIR peut avoir sur vos données, contactez votre fournisseur d'assistance principal.  
  
  
