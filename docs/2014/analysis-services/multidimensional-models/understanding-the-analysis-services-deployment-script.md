---
title: Présentation de l’analyse de Services le Script de déploiement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5473cc30dff70813c252e9529b4490962c329abb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194439"
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Description du script de déploiement Analysis Services
  Le script de déploiement XMLA généré par l’Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comporte deux sections :  
  
-   La première partie du script de déploiement contient les commandes nécessaires à la création, la modification ou la suppression des objets [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriés dans la base de données de destination. Par défaut, les fichiers d'entrée générés par le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont basés sur un déploiement incrémentiel. Par conséquent, le script de déploiement XMLA n'affecte que les objets qui ont été modifiés ou supprimés.  
  
-   La seconde partie du script de déploiement contient les commandes requises pour traiter uniquement les objets créés ou modifiés sur le serveur de destination (option Traiter par défaut) ou pour traiter intégralement la base de données de destination. Vous pouvez également décider que le script de déploiement ne contiendra aucune commande de traitement.  
  
 L'ensemble du script de déploiement peut être exécuté dans une seule transaction ou dans plusieurs transactions. Si le script est exécuté dans plusieurs transactions, la première partie du script est exécutée sous la forme d'une seule transaction, et chaque objet est traité dans sa propre transaction.  
  
> [!IMPORTANT]  
>  L’Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déploie les objets uniquement dans une seule base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Il ne déploie pas des objets, ni des données au niveau du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [L’Assistant Déploiement de Analysis Services en cours d’exécution](running-the-analysis-services-deployment-wizard.md)   
 [Présentation des fichiers d’entrée utilisés pour créer le script de déploiement](deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
