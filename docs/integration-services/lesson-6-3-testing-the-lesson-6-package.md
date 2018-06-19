---
title: 'Étape 3 : Test du package de la leçon 6 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b96f7d7f908508a8ca8e69e11ddc1fe9374f6577
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334223"
---
# <a name="lesson-6-3---testing-the-lesson-6-package"></a>Leçon 6-3 : Test du package de la leçon 6
Au moment de l'exécution, votre package obtient la valeur de la propriété Directory à partir du paramètre VarFolderName.  
  
Pour vérifier si le package met à jour la propriété Directory avec la nouvelle valeur lors de l'exécution, exécutez tout simplement le package. Étant donné que seuls trois fichiers de données exemple ont été copiés dans le nouveau répertoire, le flux de données ne sera exécuté que trois fois au lieu de parcourir les 14 fichiers du dossier d'origine.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 6 contiennent les objets affichés dans les diagrammes suivants. Le flux de contrôle doit être identique au flux de contrôle de la leçon 5. Le flux de données doit être identique au flux de données de la leçon 5.  
  
**Flux de contrôle**  
  
![Flux de contrôle](../integration-services/media/task3lesson6control.jpg "Flux de contrôle")  
  
**Flux de données**  
  
![Flux de données](../integration-services/media/task3lesson6data.jpg "Flux de données")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Pour tester le package du didacticiel de la leçon 6  
  
1.  Dans le menu Déboguer, cliquez sur Démarrer le débogage.  
  
2.  Une fois l'exécution du package terminée, dans le menu Déboguer, cliquez sur Arrêter le débogage.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Étape 4 : Déploiement du package de la Leçon 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
