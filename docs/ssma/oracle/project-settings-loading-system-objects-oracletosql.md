---
title: Paramètres (objets de système de chargement) du projet (OracleToSQL) | Documents Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2417a74ff590c0eacae367bc1f048ed912b82988
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777795"
---
# <a name="project-settingsloading-system-objects-oracletosql"></a>Paramètres (objets de système de chargement) du projet (OracleToSQL)
La page de chargement des objets de système de la **les paramètres de projet** boîte de dialogue vous permet de spécifier les objets du système Oracle SSMA convertit et les charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Le volet du chargement des objets système n’est disponible dans le **les paramètres de projet** et **les paramètres de projet par défaut** boîtes de dialogue :  
  
-   Pour spécifier les paramètres pour tous les projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de la Migration** déroulante cliquez sur **général** au bas de la gauche, puis cliquez sur **du chargement des objets système**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **les paramètres de projet**, cliquez sur **général** au bas de la gauche, puis cliquez sur **du chargement des objets système**.  
  
## <a name="default-settings"></a>Paramètres par défaut  
Conversion d’objets système consomme des ressources système et du temps. Pour améliorer les performances, SSMA sélectionne uniquement les objets système plus fréquemment utilisées, comme indiqué dans la liste suivante :  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS.DBMS_UTILITY  
  
-   SYS. STANDARD  
  
-   SYS. UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS.DBMS_SESSION  
  
Si vos objets Oracle font référence aux objets système supplémentaires, vous devez sélectionner ces objets. Si vous ne sélectionnez pas les objets système qui sont référencés par vos objets de base de données Oracle, SSMA signale les erreurs de conversion. Si vous recevez des erreurs de conversion dus à l’absence d’objets système, sélectionnez les objets manquants dans cette boîte de dialogue. Vous pouvez ensuite répéter la conversion si nécessaire.  
  
