---
title: Filtrer des données dans une table de modèle tabulaire Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b1fcdda5bd49f8056a6035ec10da8fb52f1c5d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162808"
---
# <a name="filter-data-in-a-table"></a>Filtrer des données dans une table 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Vous pouvez appliquer des filtres quand vous importez des données pour contrôler les lignes chargées dans une table. Une fois les données importées, vous ne pouvez pas supprimer de lignes individuelles. Toutefois, vous pouvez appliquer des filtres personnalisés pour contrôler la façon dont les lignes sont affichées. Les lignes qui ne répondent pas à ces critères de filtrage sont masquées. Vous pouvez filtrer les données sur une ou plusieurs colonnes. Les filtres sont additifs, ce qui signifie que chaque filtre supplémentaire est basé sur le filtre actuel et réduit davantage le sous-ensemble de données.  
  
> [!NOTE]  
>  La fenêtre d'aperçu de filtre limite le nombre de valeurs différentes affichées. Si la limite est dépassée, un message s'affiche.  
  
### <a name="to-filter-data-based-on-column-values"></a>Pour filtrer des données selon les valeurs de colonne  
  
1.  Dans le générateur de modèles, sélectionnez une table, puis cliquez sur la flèche dans l'en-tête de la colonne par laquelle vous voulez effectuer le filtrage.  
  
2.  Dans le menu Filtre automatique, effectuez l'une des opérations suivantes :  
  
    -   Dans la liste de valeurs de colonne, sélectionnez ou désélectionnez une ou plusieurs valeurs sur lesquelles filtrer les données, puis cliquez sur **OK**.  
  
         Si le nombre de valeurs est très important, les éléments individuels peuvent ne pas être affichés dans la liste. Le message « Trop d'éléments à afficher » sera alors affiché.  
  
    -   Cliquez sur **Filtres de nombres** ou sur **Filtres de texte** (en fonction du type de colonne), puis cliquez sur l’une des commandes de l’opérateur de comparaison (comme **Égal à**) ou cliquez sur **Filtre personnalisé**. Dans la boîte de dialogue **Filtre personnalisé** , créez le filtre, puis cliquez sur **OK**.  
  
### <a name="to-clear-a-filter-for-a-column"></a>Pour effacer le filtre d'une colonne  
  
1.  Cliquez sur la flèche dans l'en-tête de la colonne dont vous souhaitez effacer un filtre.  
  
2.  Cliquez sur **effacer le filtre de \<nom de colonne >** .  
  
### <a name="to-clear-all-filters-for-a-table"></a>Pour effacer tous les filtres d'une table  
  
1.  Dans le générateur de modèles, sélectionnez la table dont vous souhaitez effacer les filtres.  
  
2.  Cliquez sur le menu **Colonne** , puis sur **Effacer tous les filtres**.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer et trier des données](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [Perspectives](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
