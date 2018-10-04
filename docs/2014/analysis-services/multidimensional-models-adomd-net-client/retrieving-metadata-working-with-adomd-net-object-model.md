---
title: Utilisation du modèle objet ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 46a34a3885d0db0f80fd683e2cec74b68d26797c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156539"
---
# <a name="working-with-the-adomdnet-object-model"></a>Utilisation du modèle objet ADOMD.NET
  ADOMD.NET fournit un modèle objet qui permet d'afficher les cubes et les objets subordonnés contenus dans une source de données analytiques. Toutefois, toutes les métadonnées d'une source de données analytiques spécifique ne sont pas accessibles via le modèle objet. Le modèle objet donne uniquement accès aux informations qui permettent à une application cliente de s'afficher de telle sorte que l'utilisateur puisse construire des commandes de manière interactive. Dans la mesure où la complexité des métadonnées à présenter est réduite, le modèle objet ADOMD.NET n'en est que plus facile à utiliser.  
  
 Dans le modèle objet ADOMD.NET, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> donne accès aux informations sur les cubes OLAP (Online Analytical Processing) et les modèles d'exploration de données définis dans une source de données analytiques, ainsi qu'aux objets connexes tels que les dimensions, les jeux nommés et les algorithmes d'exploration.  
  
## <a name="retrieving-olap-metadata"></a>Récupération de métadonnées OLAP  
 Chaque objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> renferme une collection d'objets <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> qui représentent les cubes accessibles à l'utilisateur ou à l'application. L'objet <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> expose les informations sur le cube, ainsi que les divers objets qui lui sont associés comme les dimensions, les indicateurs de performance clés, les mesures, les jeux nommés, etc.  
  
 Dans la mesure du possible, vous devez utiliser l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> pour représenter les métadonnées dans les applications clientes conçues pour prendre en charge plusieurs serveurs OLAP ou à des fins plus générales d'affichage et d'accès aux métadonnées.  
  
> [!NOTE]  
>  Pour des métadonnées spécifiques au fournisseur ou pour un affichage et un accès aux métadonnées détaillés, utilisez des ensembles de lignes de schéma pour récupérer les métadonnées. Pour plus d’informations, consultez [Working with Schema Rowsets in ADOMD.NET](retrieving-metadata-working-with-schema-rowsets.md)).  
  
 Dans l'exemple suivant, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> est utilisé pour récupérer les cubes visibles et leurs dimensions à partir du serveur local :  
  
 [!code-csharp[Adomd.NetClient#RetrieveCubesAndDimensions](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#retrievecubesanddimensions)]  
  
## <a name="retrieving-data-mining-metadata"></a>Récupération de métadonnées d'exploration de données  
 Chaque objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> intègre plusieurs collections qui fournissent des informations sur les possibilités de la source de données en matière d'exploration de données :  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> contient une liste de tous les modèles d'exploration de données de la source de données.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> fournit des informations sur les algorithmes d'exploration de données disponibles.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> expose des informations sur les structures d'exploration de données du serveur.  
  
 Pour déterminer comment exécuter une requête sur un modèle d'exploration de données du serveur, parcourez de manière itérative la collection <xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A>. Chaque objet <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn> présente les caractéristiques suivantes :  
  
-   si l'objet est une colonne d'entrée (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>) ;  
  
-   si l'objet est une colonne de prédiction (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>) ;  
  
-   les valeurs associées à une colonne discrète (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>) ;  
  
-   le type de données de la colonne (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>).  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de métadonnées à partir d’une source de données analytiques](retrieving-metadata-from-an-analytical-data-source.md)  
  
  
