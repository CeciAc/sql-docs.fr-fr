---
title: Rapport d’évaluation (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5525d989-024c-402d-9e84-faa4721cc5b9
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8c16c2536b47c9f5341227fa61cbd913c8052523
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "40396048"
---
# <a name="assessment-report-mysqltosql"></a>Rapport d’évaluation (MySQLToSQL)
La fenêtre de rapport d’évaluation affiche les résultats de la conversion d’objets de base de données à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, et peut également aider à vous estimer le coût et complexité de vos projets de migration.  
  
Pour accéder au rapport d’évaluation, sélectionner les objets à convertir dans l’Explorateur de métadonnées de source, avec le bouton droit **schémas**, puis sélectionnez **créer un rapport**.  
  
## <a name="options"></a>Options  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Statistiques de conversion**|Affiche les statistiques de la conversion en type d’instruction. Ce volet est visible lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Objets par catégories**|Affiche le nombre d’objets par catégorie. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Statistiques**|Affiche les statistiques de conversion de l’objet sélectionné. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche. Vous devrez peut-être développer **statistiques**, ce qui est immédiatement au-dessus du **Source** volet, pour afficher ce volet.|  
|**Source**|Affiche le code de MySQL pour l’objet sélectionné et met en évidence de code qui n’a pas été converti à [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.|  
|**Cible**|Montre la conversion du résultant [!INCLUDE[tsql](../../includes/tsql-md.md)] code pour l’objet sélectionné et les messages d’erreur pour le code qui ne sont pas converties. Ce volet est visible uniquement lorsqu’un objet avec le code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour naviguer dans le code.|  
|**Volet messages**|Affiche les erreurs, avertissements et les messages d’information qui ont été générées lors de la création du rapport d’évaluation. Les messages sont regroupés par numéro. Pour afficher le code qui a provoqué l’erreur, cliquez sur **erreurs**, **avertissements**, ou **Info**, développez la catégorie de messages, puis cliquez sur un message.|  
  
