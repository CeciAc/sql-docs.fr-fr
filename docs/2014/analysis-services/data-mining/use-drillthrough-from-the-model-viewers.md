---
title: Utiliser l’extraction des visionneuses de modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebb910af4a9c01784fb74195ad6eed0f7f96db71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66082835"
---
# <a name="use-drillthrough-from-the-model-viewers"></a>Utiliser l'extraction des visionneuses de modèle
  Selon le type de modèle, vous pouvez utiliser l'extraction des visionneuses d'exploration sur l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données pour explorer les cas utilisés dans le modèle d'exploration de données ou pour afficher des colonnes supplémentaires de la structure d'exploration de données. Bien que de nombreux types de modèles ne prennent pas en charge l'extraction, car les séquences du modèle ne peuvent pas être directement liées à des cas spécifiques, les types de modèles suivants prennent en charge l'extraction.  
  
 Notez que l'extraction doit avoir été activée sur le modèle, et vous devez disposer des autorisations appropriées. L'option d'extraction peut également être désactivée si le modèle est dans un état non traité, que le modèle ait été traité précédemment et comporte un contenu ou non. Pour récupérer des données de cas de modèle à l'aide de l'extraction, le cache de la structure et le modèle doivent être actifs.  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a>Utiliser l'extraction dans la Visionneuse d'arborescences Microsoft  
  
1.  Dans le Concepteur d'exploration de données, sélectionnez un modèle d'arbre de décision, puis sélectionnez **Parcourir le modèle** pour ouvrir le modèle dans la **Visionneuse d'arborescences Microsoft**. Dans SQL Server Management Studio, cliquez avec le bouton droit sur le modèle, puis sélectionnez **Parcourir**.  
  
2.  Cliquez avec le bouton droit sur un nœud dans le graphique d’arbre, puis sélectionnez **Extraire**.  
  
3.  Sélectionnez l'une des options suivantes : **Colonnes de modèle uniquement** ou **modéliser et de colonnes de Structure**. Si vous n'avez pas d'autorisations, une option peut ne pas être disponible.  
  
4.  La boîte de dialogue **Extraire** s’ouvre, affichant les données de cas et/ou de structure. La barre de titre de la boîte de dialogue contient également une description qui identifie le nœud dont la requête d'extraction a été exécutée.  
  
5.  Cliquez avec le bouton droit n’importe où dans les résultats et sélectionnez **Copier tout** pour enregistrer les résultats dans le Presse-papiers.  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a>Utiliser l'extraction dans Microsoft Cluster Viewer  
  
1.  Dans le Concepteur d'exploration de données, sélectionnez un modèle de clustering, puis sélectionnez **Parcourir le modèle** pour ouvrir le modèle dans **Microsoft Cluster Viewer**. Dans SQL Server Management Studio, cliquez avec le bouton droit sur le modèle, puis sélectionnez **Parcourir**.  
  
2.  Sous l’onglet **Cluster** , cliquez avec le bouton droit sur n’importe quel nœud.  
  
3.  Sélectionnez **extraction**, puis sélectionnez une des options suivantes : **Colonnes de modèle uniquement** ou **modéliser et de colonnes de Structure**. Si vous n'avez pas d'autorisations, une option peut ne pas être disponible.  
  
4.  La boîte de dialogue **Extraire** s’ouvre, affichant les données de cas et/ou de structure. La barre de titre de la boîte de dialogue contient également une description qui identifie le cluster pour les cas.  
  
5.  Cliquez avec le bouton droit n’importe où dans les résultats et sélectionnez **Copier tout** pour enregistrer les résultats dans le Presse-papiers.  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a>Utiliser l'extraction dans la Visionneuse de l'algorithme MAR (Microsoft Association Rules)  
  
1.  Dans le Concepteur d'exploration de données, sélectionnez un modèle d'association, puis sélectionnez **Parcourir le modèle** pour ouvrir le modèle dans la **Visionneuse de l'algorithme MAR (Microsoft Association Rules)** . Dans SQL Server Management Studio, cliquez avec le bouton droit sur le modèle, puis sélectionnez **Parcourir**.  
  
2.  Sous l’onglet **Règles** , cliquez avec le bouton droit sur une ligne qui représente une règle. Dans l'onglet **Jeux d'éléments** , cliquez sur n'importe quelle ligne qui contient un jeu d'éléments.  
  
3.  Sélectionnez **extraction**, puis sélectionnez une des options suivantes : **Colonnes de modèle uniquement** ou **modéliser et de colonnes de Structure**. Si vous n'avez pas d'autorisations, une option peut ne pas être disponible.  
  
4.  La boîte de dialogue **Extraire** s’ouvre, affichant les données de cas et/ou de structure. La barre de titre de la boîte de dialogue contient également une description qui identifie le nom de la règle.  
  
5.  Cliquez avec le bouton droit n’importe où dans les résultats et sélectionnez **Copier tout** pour enregistrer les résultats complets du cas dans le Presse-papiers. Vous pouvez également sélectionner **Copier** pour copier uniquement le cas sélectionné. Si le modèle contient une colonne de table imbriquée, seul le nom de la colonne de table imbriquée est collé ; pour extraire les valeurs de données de la colonne de table imbriquée pour chaque cas vous devez créer une requête sur le contenu.  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a>Utiliser l'extraction dans la Visionneuse de l'algorithme MSC (Microsoft Sequence Cluster)  
  
1.  Dans le Concepteur d'exploration de données, sélectionnez un modèle de clustering, puis sélectionnez **Parcourir le modèle** pour ouvrir le modèle dans **Microsoft Cluster Viewer**. Dans SQL Server Management Studio, cliquez avec le bouton droit sur le modèle, puis sélectionnez **Parcourir**.  
  
2.  Sous l’onglet **Diagramme de cluster**, cliquez avec le bouton droit sur n’importe quel nœud qui représente un cluster. Dans l'onglet **Profils du cluster** , cliquez n'importe où dans un profil de cluster ou dans le cluster représentant la totalité de la population du modèle.  
  
3.  Sélectionnez **extraction**, puis sélectionnez une des options suivantes : **Colonnes de modèle uniquement** ou **modéliser et de colonnes de Structure**. Si vous n'avez pas d'autorisations, une option peut ne pas être disponible.  
  
4.  La boîte de dialogue **Extraire** s’ouvre, affichant les données de cas et/ou de structure. La barre de titre de la boîte de dialogue contient également une description qui identifie le cluster pour les cas.  
  
5.  Cliquez avec le bouton droit n’importe où dans les résultats et sélectionnez **Copier tout** pour enregistrer les résultats dans le Presse-papiers. Si le modèle contient une colonne de table imbriquée, seul le nom de la colonne de table imbriquée est collé ; pour extraire les valeurs de données de la colonne de table imbriquée pour chaque cas vous devez créer une requête sur le contenu.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)   
 [Extraction sur des modèles d'exploration de données](drillthrough-on-mining-models.md)   
 [Extraction sur des structures d'exploration de données](drillthrough-on-mining-structures.md)  
  
  
