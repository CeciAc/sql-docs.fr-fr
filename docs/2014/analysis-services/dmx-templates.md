---
title: Modèles DMX | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3bf7682ce42422efb0e47e4272e53933eba92a4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081558"
---
# <a name="dmx-templates"></a>Modèles DMX
  Les modèles d'exploration de données vous aident à créer rapidement des requêtes sophistiquées. Bien que la syntaxe générale des requêtes DMX soit bien documentée, l'utilisation de modèles facilite leur création car il suffit de cliquer et pointer sur les arguments et les sources de données.  
  
## <a name="using-the-templates"></a>L’aide de modèles  
  
1.  Dans le Client d’exploration de données pour Excel, cliquez sur **requête**.  
  
2.  Dans l’Assistant **Démarrer** , cliquez sur **suivant**.  
  
3.  Dans la page, **sélectionner un modèle**, cliquez sur **avancé**.  
  
     **Conseil :** Si vous vous apprêtez à créer une requête de prédiction sur un modèle, vous pouvez tout d’abord sélectionner le modèle, puis cliquez sur **avancé**, pour préremplir le modèle avec le nom du modèle.  
  
4.  Dans le **éditeur de requêtes d’avancé d’exploration de données**, cliquez sur **modèles DMX**, puis sélectionnez un modèle.  
  
5.  Appuyez sur ENTRÉE pour charger le modèle dans le volet de Requête DMX.  
  
6.  Cliquez ensuite sur les liens dans le modèle, et quand la boîte de dialogue apparaît, sélectionnez un résultat, un modèle, ou un paramètre approprié.  
  
     Pour les requêtes de prédiction, choisissez le dataset d'entrée en premier, puis mappez les colonnes.  
  
7.  Cliquez sur **modifier la requête** pour basculer vers l’affichage de l’éditeur de texte et de modifier manuellement la requête.  
  
     Sachez cependant que si vous passez d'un affichage à l'autre lorsque vous utilisez l'éditeur de requêtes, toutes les informations figurant dans l'affichage précédent seront effacées. Avant de changer d'affichage, enregistrez votre travail en copiant les instructions DMX et en les collant dans un autre fichier.  
  
8.  Cliquez sur **Terminer**. Dans le **choisir une Destination** boîte de dialogue, spécifiez où vous souhaitez enregistrer les résultats. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Si vous avez exécuté une instruction avec succès, l’instruction DMX que vous avez envoyé au serveur est également enregistrée dans le **Trace** fenêtre. Pour plus d’informations sur l’utilisation de la fonctionnalité de Trace, consultez [Trace &#40;Client d’exploration de données pour Excel&#41;](trace-data-mining-client-for-excel.md).  
  
 Pour plus d’informations sur la façon d’utiliser les données d’exploration de données éditeur de requêtes avancé, consultez [requête &#40;SQL Server Data Mining Add-ins&#41; ](query-sql-server-data-mining-add-ins.md) et [éditeur de requêtes d’exploration de données avancé](advanced-data-mining-query-editor.md).  
  
## <a name="list-of-dmx-templates"></a>Liste des modèles DMX  
 Les modèles DMX suivants sont inclus dans le Client d'exploration de données pour Excel.  
  
 **Prediction**  
  
 Utilisez ces modèles pour créer des requêtes de prédiction avancées, notamment des requêtes non prises en charge par les Assistants des compléments, par exemple les requêtes qui utilisent des tables imbriquées ou des sources de données externes.  
  
-   Prédictions filtrées  
  
-   Prédictions imbriquées filtrées  
  
-   Prédictions imbriquées  
  
-   Prédictions singleton  
  
-   Prédictions standard  
  
-   Prédictions de série chronologique  
  
-   Requête de prédiction TOP  
  
-   Requête de prédiction TOP sur la table imbriquée  
  
 **Créer**  
  
 Utilisez ces modèles pour créer des modèles ou des structures de données personnalisés. Vous n’êtes pas limité aux modèles pris en charge par les Assistants, vous pouvez utiliser n’importe quel algorithme d’exploration de données pris en charge par l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] auquel vous êtes connecté, y compris les algorithmes de plug-in.  
  
-   Modèle de Mining  
  
-   Structure d'exploration de données  
  
-   Structure d'exploration de données avec données d'exclusion  
  
-   Modèle temporaire  
  
-   Structure temporaire  
  
 **Propriétés d’un modèle**  
  
 Utilisez ces modèles pour créer des requêtes qui obtiennent des métadonnées sur le modèle et le jeu d'apprentissage. Récupérez également les détails du contenu du modèle, ou obtenez un profil statistique des données d'apprentissage.  
  
-   Contenu du modèle d’exploration de données  
  
-   Valeurs minimale et maximale de la colonne  
  
-   Cas d'apprentissage/scénarios de test de la structure d'exploration de données  
  
-   Valeurs de colonnes discrètes  
  
 **Gestion**  
  
 Utilisez ces modèles pour effectuer toutes les tâches de gestion prises en charge par DMX, notamment pour importer et exporter des modèles, ou pour supprimer et nettoyer des modèles ou des structures de données.  
  
-   Effacer le modèle d'exploration de données  
  
-   Effacer la structure et des modèles  
  
-   Effacer la structure d'exploration de données  
  
-   Supprimer le modèle d'exploration de données  
  
-   Supprimer la structure d'exploration de données  
  
-   Renommer le modèle d'exploration de données  
  
-   Renommer la structure d'exploration de données  
  
-   Effectuer l'apprentissage du modèle d'exploration de données  
  
-   Effectuer l'apprentissage d'une structure d'exploration de données imbriquée  
  
-   Effectuer l'apprentissage d'une structure d'exploration de données  
  
### <a name="requirements"></a>Configuration requise  
 En fonction du modèle vous utilisez, vous pouvez avoir besoin d'autorisations administratives pour accéder au serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et exécuter la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)  
  
  
