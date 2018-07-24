---
title: Placer des étiquettes dans un graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 0eabbd703d04e5aca74b8b94e449d5d8fd18ae97
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261995"
---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a>Placer des étiquettes dans un graphique (Générateur de rapports et SSRS)
  Chaque type de graphique ayant une forme différente, les étiquettes de point de données sont positionnées de manière optimale de façon à ne pas interférer sur le graphique. La position par défaut des étiquettes varie en fonction du type de graphique :  
  
-   Sur les graphiques empilés, les étiquettes peuvent être uniquement être positionnées à l'intérieur de la série.  
  
-   Sur les graphiques en entonnoir ou en pyramide, les étiquettes sont placées à l'extérieur d'une colonne.  
  
-   Sur les graphiques à secteurs, les étiquettes sont placées à l'intérieur des différents secteurs.  
  
-   Sur les graphiques à barres, les étiquettes sont placées en dehors des barres qui représentent les points de données.  
  
-   Sur les graphiques polaires, les étiquettes sont placées en dehors de la zone circulaire qui représente les points de données.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a>Pour modifier la position des étiquettes de point dans un graphique à secteurs  
  
1.  Créez un graphique à secteurs.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**.  
  
4.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés du graphique sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Général** , développez le nœud **CustomAttributes** . Une liste des attributs du graphique à secteurs s'affiche.  
  
6.  Sélectionnez une valeur pour la propriété PieLabelStyle.  
  
### <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a>Pour modifier la position des étiquettes de point dans un graphique en entonnoir ou en pyramide  
  
1.  Créez un graphique en entonnoir ou en pyramide.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**  
  
4.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés du graphique sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Général** , développez le nœud **CustomAttributes** . Une liste des attributs du graphique en entonnoir s'affiche.  
  
6.  Pour un graphique en entonnoir, sélectionnez une valeur pour la propriété FunnelLabelStyle. Pour un graphique en pyramide, sélectionnez une valeur pour la propriété PyramidLabelStyle.  
  
    > [!NOTE]  
    >  Lorsque cette propriété est définie sur une valeur `OutsideInColumn`, les étiquettes sont dessinées dans une colonne verticale. Il est impossible de modifier la position de la colonne.  
  
### <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a>Pour modifier la position des étiquettes de point dans un graphique à barres  
  
1.  Créez un graphique à barres.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**  
  
4.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés du graphique sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Général** , développez le nœud **CustomAttributes** . Une liste des attributs du graphique à barres s'affiche.  
  
6.  Sélectionnez une valeur pour la propriété BarLabelStyle.  
  
 Lorsque la barre de style de l’étiquette est définie sur `Outside`, les étiquettes sont placées en dehors de la barre, tant qu’elles s’ajustent à la zone de graphique. Si l'étiquette ne peut pas être placée en dehors de barre mais dans la zone du graphique, elle est placée à l'intérieur de la barre à la position la plus proche de l'extrémité de la barre.  
  
### <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a>Pour modifier la position des étiquettes de point dans un graphique à secteurs, un histogramme, un graphique en courbes ou un graphique à nuage de points  
  
1.  Créez un graphique à secteurs, un histogramme, un graphique en courbes ou un graphique à nuage de points.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**  
  
4.  Sur l'aire de conception, cliquez sur la série. Les propriétés de la série sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Données** , développez le nœud **DataPoint** , puis le nœud **Étiquette**.  
  
6.  Sélectionnez une valeur pour la propriété Position.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques en secteurs &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Graphiques à barres &#40;Générateur de rapports et SSRS&#41;](bar-charts-report-builder-and-ssrs.md)   
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Mettre en forme les étiquettes des axes en tant que dates ou devises &#40;Générateur de rapports et SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Étiquettes de Point de données d’affichage à l’extérieur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  