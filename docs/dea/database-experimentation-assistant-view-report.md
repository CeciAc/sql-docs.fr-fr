---
title: Afficher les rapports d’analyse pour les mises à niveau de SQL Server
description: Afficher les rapports d’analyse dans Assistant Expérimentation de base de données
ms.custom: seo-lt-2019
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: b72d49e691311104481637ff49d6c1e09ae0c230
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74317742"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Afficher les rapports d’analyse dans Assistant Expérimentation de base de données

Une fois que vous avez utilisé Assistant Expérimentation de base de données (DEA) pour [créer un rapport d’analyse](database-experimentation-assistant-create-report.md), suivez les étapes ci-dessous pour examiner le rapport pour obtenir des informations sur les performances en fonction de votre test A/B.

## <a name="select-a-server"></a>Sélectionnez un serveur.

Dans DEA, sélectionnez l’icône de menu. Dans le menu développé, sélectionnez **rapports d’analyse** en regard de l’icône de liste de vérification pour ouvrir la fenêtre rapports d’analyse.

Sous **rapports d’analyse**, entrez le nom d’un ordinateur exécutant SQL Server qui a une base de données d’analyse, puis sélectionnez **se connecter**.

![Se connecter à un rapport existant](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

Si vous ne disposez pas de dépendances, la page **Configuration requise** vous invite à entrer des liens pour les installer. Si nécessaire, installez les composants requis, puis sélectionnez **Réessayer**.

![Page conditions préalables](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>Sélectionner un rapport d’analyse à afficher

Dans la liste des rapports d’analyse, double-cliquez sur un rapport pour l’ouvrir.

![Afficher le rapport existant](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

Vous pouvez vous familiariser avec la représentation de votre charge de travail, comme illustré dans cet exemple de graphique :

![Graphiques de représentation des charges de travail](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>Afficher et comprendre le rapport d’analyse

Cette section vous guide tout au long du rapport d’analyse.

### <a name="query-categories"></a>Catégories de requêtes

Sélectionnez les différents secteurs du graphique à secteurs de gauche pour afficher uniquement les requêtes qui appartiennent à cette catégorie.

![Secteurs de rapport](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- **Requêtes dégradées**: requêtes qui ont été améliorées dans un par rapport à B.  
- **Erreurs**: requêtes qui affichent des erreurs dans l’instance B, mais pas dans l’instance A.  
- **Requêtes améliorées**: requêtes qui s’exécutaient mieux dans l’instance B que dans l’instance A.  
- **Requêtes indéterminées**: requêtes qui ont subi une modification de performance indéterminée.  
- **Identique**: requêtes dans lesquelles les performances sont restées les mêmes sur les instances A et B.

### <a name="individual-query-drill-down"></a>Exploration des requêtes individuelles

Vous pouvez sélectionner les liens du modèle de requête pour afficher des informations plus détaillées sur des requêtes spécifiques.

![Exploration des requêtes](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

Sélectionnez une requête spécifique pour ouvrir un résumé de comparaison de la requête.

![Résumé de la comparaison](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

Vous pouvez voir les instances A et B sur lesquelles la requête s’est exécutée. Vous pouvez également voir un modèle de ce à quoi la requête peut ressembler. Un tableau affiche des informations de requête spécifiques aux instances A et B.

### <a name="error-queries"></a>Requêtes d’erreur

Le rapport Résumé de la comparaison contient des sections informations d' **erreur** et informations **sur le plan de requête** développables. Les sections affichent les erreurs et les informations de plan pour les deux instances.

Sélectionnez le secteur d’erreur (rouge) pour afficher les types d’erreurs suivants :

- **Erreurs existantes**: erreurs qui se trouvaient dans un.
- **Nouvelles Erreurs**: erreurs qui se trouvaient dans B.
- **Erreurs résolues**: erreurs qui se trouvaient dans un mais pas dans B.

![Graphiques d’erreur](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="see-also"></a>Voir aussi

- Pour savoir comment générer un rapport d’analyse à partir d’une invite de commandes, consultez [exécuter à l’invite de commandes](database-experimentation-assistant-run-command-prompt.md).
