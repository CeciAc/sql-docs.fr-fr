---
title: 'Leçon 3 : À l’aide de l’utilitaire d’invite de commandes dta | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e2881a2a118306f9d567236516f05bb29ad2d60a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68186571"
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a>Leçon 3 : Utilisation de l’utilitaire de ligne de commande dta
  L’utilitaire en ligne de commande **dta** offre une fonctionnalité supplémentaire par rapport à celles fournies par l’Assistant Paramétrage du moteur de base de données.  
  
 Vous pouvez utiliser vos outils XML favoris pour créer des fichiers d'entrée pour l'utilitaire en utilisant le schéma XML de l'Assistant Paramétrage du moteur de base de données. Ce schéma est installé lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et se trouve à : C:\Program fichiers (x86) \Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd.  
  
 Le schéma XML de l'Assistant Paramétrage du moteur de base de données est également disponible en ligne sur ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).  
  
 Ce schéma offre plus de souplesse pour définir les options de paramétrage. Par exemple, il permet d'effectuer des analyses de scénarios. Pour réaliser des analyses de scénarios, vous devez spécifier un ensemble de structures de création physiques existantes ou hypothétiques pour la base de données que vous souhaitez paramétrer, puis l'analyser avec l'Assistant Paramétrage du moteur de base de données pour déterminer si cette structure de création physique hypothétique améliorera les performances de traitement des requêtes. Ce type d'analyse permet d'évaluer la nouvelle configuration sans devoir l'implémenter. Si votre structure de création physique hypothétique ne permet pas d'obtenir les améliorations souhaitées en matière de performances, il est facile de la modifier et de l'analyser de nouveau jusqu'à ce que vous ayez atteint la configuration qui produit les résultats requis.  
  
 De plus, en utilisant le schéma XML de l’Assistant Paramétrage du moteur de base de données et l’utilitaire en ligne de commande **dta** , vous pouvez intégrer la fonctionnalité de l’Assistant Paramétrage du moteur de base de données aux scripts et l’utiliser avec d’autres outils de création de base de données.  
  
 Cette leçon ne couvre pas l'utilisation de la fonction d'entrée XML de l'Assistant Paramétrage du moteur de base de données.  
  
 Cette leçon présente la syntaxe de base de l’utilitaire de ligne de commande **dta** , explique comment accéder à l’aide et propose des exercices portant sur le paramétrage de charges de travail simples.  
  
 Elle contient les rubriques suivantes :  
  
-   Démarrage de l'utilitaire en ligne de commande **dta** et paramétrage d'une charge de travail  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Démarrage de l'utilitaire de ligne de commande dta et paramétrage d'une charge de travail](lesson-1-1-tuning-a-workload.md)  
  
  
