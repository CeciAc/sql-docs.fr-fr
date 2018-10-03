---
title: MSSQLSERVER_511 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e846917005c72a0210442b5f884a5f31921cba02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857267"
---
# <a name="mssqlserver511"></a>MSSQLSERVER_511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|511|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|ROW_TOOBIG|  
|Texte du message|Impossible de créer une ligne de dimension %d supérieure au maximum autorisé %d.|  
  
## <a name="explanation"></a>Explication  
L'opération que vous avez tentée a dépassé la taille maximale d'une ligne. Habituellement, la taille maximale d'une ligne est 8 060 octets. Certains formats de stockage contiennent une surcharge susceptible de réduire la taille de ligne disponible pour les données. Par exemple, lorsque vous utilisez des colonnes éparses, la taille maximale d'une ligne est 8 018 octets. Certaines opérations qui ajoutent ou suppriment des lignes et certaines opérations qui modifient le type de données d'une colonne exigent que la ligne soit réécrite dans la page de données et que la ligne d'origine soit ensuite supprimée. Dans ces opérations, la limite effective de la taille de la ligne correspond à la moitié de la limite maximale. Cela est dû au fait que la ligne d'origine et la ligne modifiée doivent toutes les deux être incluses dans la page de données pour une courte période.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Si cela est possible, réduisez la taille de la ligne.  
  
Si vous pensez que le problème provient d'une mise à jour sur place de la ligne, vous devez modifier la table en plusieurs étapes. Créez une nouvelle table et transférez les données dans la nouvelle table. Ensuite, supprimez la table d'origine et renommez la nouvelle table, ou tronquez la table d'origine, modifiez les lignes dans la table d'origine, puis replacez les données dans cette table.  
  
