---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: cb36765216f906b92cdd6b87e7890b94f3b15d37
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153955"
---
# <a name="mssqlserver948"></a>MSSQLSERVER_948
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|948|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|N/A|  
|Texte du message|La base de données '%.*ls' ne peut pas être ouverte, car sa version est %d. Ce serveur prend en charge la version %d et les versions précédentes. Un chemin de mise à niveau vers une version antérieure n'est pas pris en charge.|  
  
## <a name="explanation"></a>Explication  
 Certaines fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affectent la structure des fichiers de base de données. Lorsque vous attachez une base de données à une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le format de fichier peut ne pas être compatible avec une autre version du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Par exemple, cette erreur peut se produire si vous utilisez le format de stockage vardecimal dans une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis que vous essayez d'attacher les fichiers de base de données dans une version antérieure à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Identifiez la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécute sur le serveur d'origine. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], soit le serveur d’avec le bouton droit, puis cliquez sur **propriétés** ou type `SELECT @@VERSION` dans une fenêtre de requête. Ouvrez la base de données en utilisant la version d'origine de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Examinez les fonctionnalités qui sont activées sur la base de données d'origine dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Modifiez ces paramètres de façon à utiliser la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle la base de données sera attachée.  
  
  