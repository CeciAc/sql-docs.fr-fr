---
title: Rapports générés interactifs (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: caf23eb7e7d0e06a9e79dbaa6b9a0120725a4b10
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031050"
---
# <a name="clickthrough-reports-ssrs"></a>Rapports générés interactifs (SSRS)
  Dans le Générateur de rapports, un rapport généré interactif est un rapport qui fournit des informations détaillées sur les données contenues dans le rapport principal. Un rapport consultable à l'aide de clics est affiché lorsque l'utilisateur clique sur des données interactives apparaissant dans le rapport principal. Ces rapports sont automatiquement générés par le serveur de rapports. En tant que concepteur de modèle, vous déterminez ce qui est affiché dans les rapports générés interactifs en définissant les propriétés `DefaultDetailAttribute` et `DefaultAggregateAttribute` que vous affectez à une entité dans le modèle de rapport.  
  
> [!NOTE]
>  Les rapports générés interactifs ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Si vous ne savez pas quelle édition de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est utilisée par votre organisation, contactez votre administrateur de base de données.  
  
## <a name="using-default-templates"></a>Utilisation de modèles par défaut  
 Par défaut, le serveur de rapports génère deux types de modèles générés interactifs pour chaque entité : un modèle à instance unique et un modèle à plusieurs instances. L'élément sur lequel vous cliquez détermine le modèle utilisé. Si la personne lisant le rapport clique sur un attribut scalaire, le modèle à instance unique est utilisé. Si la personne lisant le rapport clique sur un attribut d'agrégation, le modèle à plusieurs instances est utilisé.  
  
#### <a name="single-instance-templates"></a>Modèles à instance unique  
 Un modèle à instance unique affiche tous les attributs de l'entité cible et tous les attributs d'agrégation par défaut qui sont spécifiés pour les entités associées ayant une relation un-à-plusieurs à partir de l'entité cible. Un modèle à instance unique est similaire à l'illustration suivante.  
  
 ![Rapport généré interactif 1 à plusieurs](../media/manytooneclickthrough.gif "Rapport généré interactif 1 à plusieurs")  
  
#### <a name="multiple-instance-templates"></a>Modèles à plusieurs instances  
 Un modèle à plusieurs instances affiche uniquement les attributs de détails par défaut de l'entité cible et tous les attributs d'agrégation par défaut qui sont spécifiés pour les entités associées ayant une relation un-à-plusieurs à partir de l'entité cible. Un modèle à plusieurs instances est similaire à l'illustration suivante.  
  
 ![Rapport généré interactif 1 à plusieurs](../media/onetomanyclickthrough.gif "Rapport généré interactif 1 à plusieurs")  
  
## <a name="customizing-clickthrough-reports"></a>personnalisation de rapports consultables à l'aide de clics  
 Au lieu d'utiliser les modèles par défaut générés par le serveur de rapports, vous pouvez créer un rapport dans le Générateur de rapports et l'utiliser comme rapport généré interactif personnalisé. Vous pouvez ensuite lier votre rapport au modèle en tant que rapport d'extraction dans le Gestionnaire de rapports.  
  
 Pour transformer un rapport du Générateur de rapports en un rapport généré interactif, vous devez activer l’option **Activer l’extraction dans ce rapport** dans la boîte de dialogue **Propriétés** du Générateur de rapports. Une fois cette option activée, un paramètre d'extraction est ajouté au rapport et ce dernier ne peut plus être exécuté directement dans le Générateur de rapports. Le paramètre d'extraction est automatiquement calculé par le serveur de rapports lorsque le lecteur du rapport clique sur un élément dans un rapport du Générateur de rapports.  
  
> [!IMPORTANT]  
>  L'entité principale ou de base employée dans le rapport doit être celle à laquelle vous liez le rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Lier un rapport à un modèle en tant que rapport généré interactif](../link-a-report-to-a-model-as-a-clickthrough-report.md)  
  
  
