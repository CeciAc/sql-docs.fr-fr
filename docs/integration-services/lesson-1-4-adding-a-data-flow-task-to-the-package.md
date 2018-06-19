---
title: 'Étape 4 : Ajout d’une tâche de flux de données au package | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e15337b25cfa8b03a5283d95c974f6d5bc0100b1
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406251"
---
# <a name="lesson-1-4---adding-a-data-flow-task-to-the-package"></a>Leçon 1-4 : Ajout d’une tâche de flux de données au package
Après avoir créé des gestionnaires de connexions pour les données sources et de destination, la tâche suivante consiste à ajouter une tâche de flux de données à votre package. La tâche de flux de données permet d'encapsuler le moteur de flux de données qui déplace les données entre les sources et les destinations et fournit la fonctionnalité grâce à laquelle il est possible de transformer, nettoyer et modifier les données lors de leur déplacement. La tâche de flux de données est l'endroit où s'effectue la majorité du travail d'un processus d'extraction, de transformation et de chargement (ETL).  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sépare le flux de données du flux de contrôle.  
  
### <a name="to-add-a-data-flow-task"></a>Pour ajouter une tâche de flux de données  
  
1.  Cliquez sur l'onglet **Flux de contrôle** .  
  
2.  Dans la **Boîte à outils SSIS**, développez **Favoris**, puis faites glisser une **tâche de flux de données** sur l’aire de conception de l’onglet **Flux de contrôle** .  
  
    > [!NOTE]  
    > Si la boîte à outils SSIS n'est pas disponible, dans le menu principal, sélectionnez SSIS, puis Boîte à outils SSIS pour afficher cette dernière.  
  
3.  Dans la zone de conception **Flux de contrôle** , cliquez avec le bouton droit sur la nouvelle **tâche de flux de données**, cliquez sur **Renommer**et changez le nom en **Extract Sample Currency Data**.  
  
    Il est préférable d'affecter des noms uniques aux composants que vous ajoutez à une zone de conception. Afin d'utiliser et de maintenir les composants plus facilement, il est conseillé de leur affecter des noms décrivant les fonctions qu'ils effectuent. Le respect de ces consignes de nommage permet une auto-documentation de vos packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . L'autre méthode permettant de documenter vos packages, consiste à utiliser des annotations. Pour plus d’informations sur les annotations, consultez [Utilisation des annotations dans les packages](../integration-services/use-annotations-in-packages.md).  
  
4.  Cliquez avec le bouton droit sur la tâche de flux de données, cliquez sur **Propriétés**puis, dans la fenêtre Propriétés, vérifiez que la propriété **LocaleID** est définie sur **Anglais (États-Unis)**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Étape 5 : Ajout et configuration de la source de fichier plat](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a> Voir aussi  
[tâche de flux de données](../integration-services/control-flow/data-flow-task.md)  
  
  
  
