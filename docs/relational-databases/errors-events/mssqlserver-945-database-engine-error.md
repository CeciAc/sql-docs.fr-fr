---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2715f20915a0bc36eaee6e5f9bf82dbded7b51ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831297"
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|945|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DB_IS_SHUTDOWN|  
|Texte du message|La base de données '%.*ls' ne peut pas être ouverte, car des fichiers sont inaccessibles, ou la mémoire ou l'espace disque sont insuffisants.  Pour plus d’informations, consultez le journal des erreurs de SQL Server.|  
  
## <a name="explanation"></a>Explication  
Il n'a pas été possible d'accéder à la base de données car il manque des fichiers ou d'autres ressources.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez le journal des erreurs pour trouver des informations supplémentaires sur les problèmes de mémoire, d'espace disque ou d'autorisation. Vérifiez l’emplacement des fichiers .mdf et .ndf de la base de données affectée et assurez-vous que le compte utilisé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est autorisé à accéder à ces fichiers. Après avoir corrigé le problème, redémarrez la base de données en utilisant l'instruction ALTER DATABASE pour la mettre en ligne (ONLINE).  
  
