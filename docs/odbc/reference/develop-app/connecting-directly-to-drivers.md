---
title: Se connecter directement à des pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44b9de304069849e965fc335e130ae57d9ec8bad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083165"
---
# <a name="connecting-directly-to-drivers"></a>Connexion directe à des pilotes
Comme expliqué dans [choisir une Source de données ou le pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), plus haut dans cette section, certaines applications ne souhaitez pas utiliser une source de données du tout. Au lieu de cela, ils souhaitent se connecter directement à un pilote. **SQLDriverConnect** offre un moyen de l’application pour se connecter directement à un pilote sans spécifier une source de données. Conceptuellement, une source de données temporaire est créée au moment de l’exécution.  
  
 Pour vous connecter directement à un pilote, l’application spécifie la **pilote** mot clé dans la chaîne de connexion à la place de la **DSN** mot clé. La valeur de la **pilote** mot clé est la description du pilote tel que retourné par **SQLDrivers**. Par exemple, un pilote a la description du pilote Paradox et exige que le nom d’un répertoire contenant les fichiers de données. Pour vous connecter à ce pilote, l’application peut utiliser une des chaînes de connexion suivantes :  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Avec la première chaîne, le pilote serait inutile des informations supplémentaires. Avec la deuxième chaîne, le pilote doit demander le nom du répertoire contenant les fichiers de données.
