---
title: Installation du Conseiller de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f70d1cbb879f8fc91e48478fb820b71b51bfd2d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094314"
---
# <a name="installing-upgrade-advisor"></a>Installation du Conseiller de mise à niveau
  L'emplacement d'installation du Conseiller de mise à niveau SQL Server 2014 dépend des éléments que vous allez analyser. Le Conseiller de mise à niveau prend en charge l'analyse à distance de tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'exception de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous n'analysez pas d'instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer le Conseiller de mise à niveau sur n'importe quel ordinateur pouvant se connecter à vos instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et répondant à la [Upgrade Advisor Prerequisites](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md). Si vous analysez des instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez installer le Conseiller de mise à niveau sur le serveur de rapports.  
  
 Exécutez le fichier **SQLUA.msi** pour installer le Conseiller de mise à niveau. L’invite de commandes vous permet d’effectuer des installations automatisées et sans assistance. Consultez [Installing Upgrade Advisor from the Command Prompt](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) pour la syntaxe et des exemples.  
  
 Obtenir SQLUA.msi :  
  
-   Dans le dossier **redist** du support du produit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Dans le cadre du [téléchargement de SQL 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Désinstallation du Conseiller de mise à niveau  
 Vous pouvez désinstaller le Conseiller de mise à niveau à l'aide de la fonction **Ajout/Suppression de programmes**. La syntaxe de l’invite de commandes prend également en charge la suppression/désinstallation.  
  
  
