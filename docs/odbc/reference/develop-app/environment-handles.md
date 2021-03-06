---
title: Handles d’environnement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 409b2c14282238766457d349287f65d90fe463b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114323"
---
# <a name="environment-handles"></a>Handles d’environnement
Un *environnement* est un contexte global d’accès aux données ; est associée à un environnement à toutes les informations qui est globales par nature, telles que :  
  
-   État de l’environnement  
  
-   Les diagnostics de niveau de l’environnement actuels  
  
-   Les handles de connexions actuellement allouées sur l’environnement  
  
-   Les paramètres actuels de chaque attribut de l’environnement  
  
 Au sein d’un morceau de code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote), un handle d’environnement identifie une structure destinée à contenir ces informations.  
  
 Handles d’environnement ne sont pas utilisés fréquemment dans les applications ODBC. Ils sont toujours utilisés dans les appels à **SQLDataSources** et **SQLDrivers** et parfois utilisés dans les appels à **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, et **SQLGetDiagRec**.  
  
 Chaque partie du code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote) contient un ou plusieurs handles d’environnement. Par exemple, le Gestionnaire de pilotes conserve un handle d’environnement distinct pour chaque application qui y est connecté. Handles d’environnement sont allouées avec **SQLAllocHandle** et libéré avec **SQLFreeHandle**.
