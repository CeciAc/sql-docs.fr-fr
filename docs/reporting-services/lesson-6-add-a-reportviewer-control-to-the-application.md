---
title: 'Leçon 6 : ajouter un contrôle ReportViewer à l’application | Microsoft Docs'
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a3892815dee3002e06abf6c76e4604225a29749a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777347"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Leçon 6 : Ajouter un contrôle ReportViewer à l'application
Après avoir conçu le rapport enfant à l'aide de l'Assistant Rapport, l'étape suivante consiste à ajouter un contrôle ReportViewer à l'application de site Web. Si vous utilisez le site web des rapports ASP.NET, la page default.aspx contient le contrôle ReportViewer.   
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Pour ajouter un contrôle ReportViewer à l'application  
  
1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Default.aspx**, puis sélectionnez **Concepteur de vues**.  
  
2.  Si la page default.aspx contient déjà le contrôle ReportViewer, passez à **l’étape 4**. Sinon, dans le groupe **Extensions AJAX** de la fenêtre **Boîte à outils** , faites glisser un contrôle **ScriptManager** vers l’aire de conception.  
  
3.  Depuis le groupe **Création de rapports** , faites glisser un contrôle **ReportViewer** vers l'aire de conception sous le contrôle **ScriptManager** .  
  
4.  Ouvrez la fenêtre **Tâches ReportViewer** en cliquant sur la flèche située dans le coin supérieur droit du contrôle **ReportViewer** .  
  
5.  Dans la zone **Choisir un rapport** , sélectionnez le rapport parent que vous avez créé.  
  
    Lorsque vous sélectionnez un rapport, les instances de sources de données utilisées dans le rapport sont créées automatiquement. Le code est généré pour instancier chaque objet DataTable (et son conteneur [DataSet](http://msdn.microsoft.com/library/system.data.dataset.aspx) ). Un contrôle [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource.aspx) est ajouté à l’aire de conception, correspondant à chaque source de données utilisée dans le rapport. Ce contrôle de source de données est configuré automatiquement.  
  
6.  Dans le menu Générer, cliquez sur Générer le site Web.  
  
    Le rapport est compilé et toutes les erreurs, comme une erreur de syntaxe dans une expression de rapport, apparaissent dans la zone **Liste d'erreurs** . Cliquez sur **Liste d'erreurs** en bas de la fenêtre de Visual Studio pour afficher la zone **Liste d'erreurs** .  
  
## <a name="next-task"></a>Tâche suivante  
Vous venez d'ajouter un contrôle ReportViewer dans l'application de site Web. Vous allez à présent ajouter une action d'extraction dans le rapport parent. Consultez [Leçon 7 : Ajouter l’action d’extraction dans le rapport parent](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md).  
  

