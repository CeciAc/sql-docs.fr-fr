---
title: Déplacement d’objets d’exploration de données | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: edbceb50dd1532e427c3bf5738dfe183223afc2d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62509871"
---
# <a name="moving-data-mining-objects"></a>Déplacement d'objets d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Les scénarios les plus courants de déplacement des objets d'exploration de données consistent à déployer un modèle d'un environnement de test ou d'analyse vers un environnement de production, ou à partager des modèles avec d'autres utilisateurs.  
  
 Cette rubrique explique comment utiliser les outils et langages de script fournis par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]pour déplacer les objets d’exploration de données.  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a>Déplacement d'objets d'exploration de données entre des bases de données ou des serveurs  
 Vous pouvez déplacer des objets d'exploration de données entre des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou entre des instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] des manières suivantes :  
  
-   Redéploiement de la solution sur une autre base de données.  
  
-   Création de scripts pour des objets individuels.  
  
-   Sauvegarde puis restauration d'une copie de la base de données.  
  
-   Exportation et importation des structures et des modèles.  
  
 La section suivante présente ces options plus en détail.  
  
### <a name="deploying"></a>Déploiement  
 Le déploiement de la solution sur un autre serveur ou une autre base de données nécessite que vous disposiez du fichier solution créé à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Pour plus d’informations sur le déploiement de solutions Analysis Services, consultez [Déployer des projets Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md).  
  
### <a name="scripting"></a>Création de scripts  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit plusieurs langages dont vous pouvez vous servir pour créer des scripts d’objets.  
  
-   **XMLA**: Vous pouvez générer un script à l’aide de XMLA en cliquant sur les objets dans des objets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour exécuter le script, ouvrez-le dans une fenêtre **Requête XMLA** sur le serveur cible.  
  
-   **DMX**: Vous pouvez créer des scripts à l’aide de modèles ou les générateurs de requêtes fournies dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Notez, toutefois, qu'il existe des différences quant aux tâches que vous pouvez effectuer avec chaque langage de script :  
  
-   Certaines propriétés telles que la description d’objet et les liaisons de données ne peuvent être créées et modifiées qu’à l’aide des langages DDL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et pas à l’aide de DMX.  
  
-   Seul DMX prend en charge l'importation et l'exportation des objets d'exploration de données.  
  
-   Seul DMX prend en charge la génération PMML ou l'importation de définitions de modèle depuis PMML.  
  
-   Seul DMX prend en charge l'apprentissage d'un modèle avec les données d'application. De plus, l'instruction DMX INSERT INTO prend en charge l'apprentissage d'un modèle sans fournir de valeurs pour une colonne clé.  
  
 Pour plus d’informations, consultez [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
### <a name="backup-and-restore"></a>Sauvegarde et restauration  
 La sauvegarde et la restauration d'une base de données Analysis Services complète est la méthode idéale si votre solution d'exploration de données repose sur des objets OLAP. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] fournit des fonctionnalités de sauvegarde et de restauration qui accélèrent et facilitent la sauvegarde des bases de données.  
  
 Pour plus d’informations sur la sauvegarde, consultez [Sauvegarde et restauration de bases de données Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
### <a name="exporting-and-importing"></a>Exportation et importation  
 L'exportation puis la réimportation des modèles et des structures d'exploration de données à l'aide d'instructions DMX est la méthode la plus facile pour déplacer ou sauvegarder des objets d'exploration de données relationnelles individuels. Pour plus d'informations sur la syntaxe DMX de ces opérations, consultez les rubriques suivantes :  
  
-   [EXPORT &#40;DMX&#41;](../../dmx/export-dmx.md)  
  
-   [IMPORT &#40;DMX&#41;](../../dmx/import-dmx.md)  
  
 Si vous spécifiez l’option INCLUDE DEPENDENCIES, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exporte également la définition des vues de source de données requises, et quand vous importez le modèle ou la structure, il recrée la vue de source de données sur le serveur cible. Lorsque vous avez terminé d'importer le modèle, n'oubliez pas de définir les autorisations d'exploration de données sur l'objet.  
  
> [!NOTE]  
>  Vous ne pouvez pas exporter et importer des modèles OLAP en utilisant DMX. Si votre modèle d’exploration de données est basé sur un cube OLAP, vous devez utiliser la fonctionnalité fournie par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour la sauvegarde et la restauration d’une base de données complète, ou redéployer le cube et ses modèles.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des solutions et des objets d'exploration de données](../../analysis-services/data-mining/management-of-data-mining-solutions-and-objects.md)  
  
  
