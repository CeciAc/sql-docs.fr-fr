---
title: Exclure les lignes dupliquées
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 4caf41fcf7c4373250b875a01c1ce733d086b60a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247249"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Exclure les doublons de lignes (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Si vous souhaitez afficher uniquement des valeurs uniques dans un jeu de résultats, vous pouvez spécifier qu'il faut exclure les doublons du jeu de résultats.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Pour exclure les doublons du jeu de résultats  
  
1.  Cliquez avec le bouton droit sur un point de l’arrière-plan du volet Schéma, puis choisissez **Propriétés** dans le menu contextuel.  
  
2.  Dans la fenêtre Propriétés, cliquez sur **Valeurs DISTINCT** et affectez-lui la valeur **Oui**.  
  
    Le Concepteur de requêtes et de vues insère le mot clé DISTINCT devant la liste des colonnes affichées dans l'instruction SQL.  
  
    > [!NOTE]  
    > Si vous utilisez le mot clé DISTINCT, il se peut que vous ne puissiez pas modifier le jeu de résultats dans le volet Résultats.  
  
## <a name="see-also"></a>Voir aussi  
[Spécifier des critères de recherche &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
