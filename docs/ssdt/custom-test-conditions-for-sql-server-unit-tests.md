---
title: Conditions de test personnalisées pour les tests unitaires SQL Server| Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 32a15d61-e908-4ae1-a238-4fd0f988d8c8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1292666a44f93d8b8dd551975eed4b7ea46f5ffe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984563"
---
# <a name="custom-test-conditions--for-sql-server-unit-tests"></a>Conditions de test personnalisées pour les tests unitaires SQL Server
Il est possible d’ajouter des conditions de test personnalisées aux tests unitaires SQL Server. Cependant, vous devez d'abord installer la condition de test pour pouvoir l'utiliser, que vous ayez créé l'extension ou que vous en installiez une créée par un autre utilisateur.  
  
Avant d'installer une condition de test que vous n'avez pas créée, vous devez connaître les risques suivants :  
  
-   Le programme d'installation de la condition de test peut être malveillant et accéder à des ressources protégées dépendant de vos autorisations d'installation.  
  
-   La condition de test elle-même peut être malveillante et prendre le contrôle des ressources protégées si l'utilisateur qui utilise l'extension dispose des autorisations nécessaires.  
  
Pour réduire le risque, vous ne devez installer une condition de test personnalisée que si elle provient d'une source connue. Si vous obtenez une condition de test auprès d'une source non approuvée, examinez son code source et son programme d'installation (le cas échéant) avant installation et utilisation.  
  
Pour installer une condition de test personnalisée, copiez l’assembly signé (.dll) dans le dossier %Program Files%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions. Si ce dossier n'existe pas, créez-le. Vous devez disposer de privilèges d'administrateur sur votre ordinateur pour effectuer une copie dans ce répertoire.  
  
> [!NOTE]  
> Il est nécessaire d’installer les versions Visual Studio 2010 et Visual Studio 2012 de la condition de test si :  
>   
> -   vous installez des conditions de test personnalisées sur un ordinateur qui peut être utilisé pour générer des tests unitaires SQL Server ;  
> -   ces tests unitaires sont utilisés dans Visual Studio 2010 et Visual Studio 2012.  
  
Pour plus d’informations sur les conditions de test personnalisées des tests unitaires SQL Server, voir :  
  
-   [Procédure : créer des conditions de test pour le Concepteur de test unitaire SQL Server](../ssdt/how-to-create-test-conditions-for-the-sql-server-unit-test-designer.md)  
  
-   [Procédure : mettre à niveau une condition de test personnalisée Visual Studio 2010 d’une version antérieure vers SQL Server Data Tools](../ssdt/how-to-upgrade-visual-studio-2010-custom-test-condition-to-ssdt.md)  
  
-   [Procédure pas à pas : utilisation d’une condition de test personnalisée pour vérifier le résultat d’une procédure stockée](../ssdt/walkthrough-use-custom-test-condition-to-verify-stored-procedure-results.md)  
  
## <a name="see-also"></a>Voir aussi  
[Vérifier le code de la base de données à l’aide de tests unitaires SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
