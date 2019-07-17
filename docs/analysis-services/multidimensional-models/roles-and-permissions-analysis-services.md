---
title: Rôles et autorisations (Analysis Services) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e6b463fedda33d8b10fbe2d1e415f1ef248ae92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165238"
---
# <a name="roles-and-permissions-analysis-services"></a>Rôles et autorisations (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit un modèle d’autorisation basé sur les rôles qui accorde l’accès aux opérations, aux objets, ainsi qu’aux données. Tous les utilisateurs qui accèdent à une instance ou à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doivent effectuer cette opération dans le contexte d’un rôle.  
  
 En tant qu’administrateur système d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous êtes chargé d’accorder l’appartenance au **rôle d’administrateur de serveur** qui donne un accès sans restrictions aux opérations sur le serveur. Ce rôle comporte des autorisations fixes et ne peut pas être personnalisé. Par défaut, les membres du groupe local Administrateurs sont automatiquement des administrateurs système d'Analysis Services.  
  
 L’accord de l’accès aux utilisateurs non-administrateurs qui interrogent ou traitent des données s’effectue par l’intermédiaire de **rôles de base de données**. Les administrateurs système et les administrateurs de base de données peuvent tous deux créer les rôles qui décrivent les différents niveaux d'accès à une base de données spécifique, puis attribuer l'appartenance à chaque utilisateur qui a besoin de l'accès. Chaque rôle dispose d'un ensemble personnalisé d'autorisations pour l'accès aux objets et aux opérations dans une base de données particulière. Vous pouvez attribuer des autorisations au niveau des bases de données, des objets intérieurs tels que les cubes et les dimensions (mais pas les perspectives) et des lignes.  
  
 Il est courant de créer des rôles et d'affecter l'appartenance en tant qu'opération distincte. Souvent, le concepteur de modèles ajoute des rôles pendant la phase de conception. De cette manière, toutes les définitions de rôles sont reflétées dans les fichiers de projet qui définissent le modèle. L'appartenance au rôle est généralement transférée ultérieurement, quand la base de données entre en production, généralement par les administrateurs de base de données qui créent des scripts pouvant être développés, testés et exécutés comme une opération indépendante.  
  
 Toutes les autorisations sont établies sur une identité d'utilisateur Windows valide. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise l’authentification Windows exclusivement pour authentifier les identités des utilisateurs. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne fournit aucune méthode d’authentification propriétaire. Consultez [Méthodologies d’authentification prises en charge par Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Les autorisations s'ajoutent pour chaque utilisateur ou groupe Windows, parmi tous les rôles de la base de données. Si un rôle interdit à un utilisateur ou à un groupe d'exécuter certaines tâches ou d'afficher certaines données, mais qu'un autre rôle lui permet de le faire, l'utilisateur ou le groupe est autorisé à exécuter la tâche ou à afficher les données.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Autorisation de l’accès à des objets et des opérations &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Octroyer des autorisations de base de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)  
  
-   [Octroyer des autorisations de cube ou de modèle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Octroyer des autorisations de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
-   [Octroyer des autorisations Lire la définition sur des métadonnées d’objets &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Octroyer des autorisations sur un objet de source de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Octroyer des autorisations sur des modèles et des structures d’exploration de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Octroyer des autorisations sur une dimension &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Octroyer un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Octroyer un accès personnalisé à des données de cellule &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer des rôles](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)  
  
  
