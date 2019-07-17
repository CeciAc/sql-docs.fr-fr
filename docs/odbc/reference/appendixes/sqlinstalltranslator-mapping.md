---
title: SQLInstallTranslator, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6433df796c88abd7873915266d1a2ca4041a5c62
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125726"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator, mappage
Lorsqu’une application ODBC *2.x* application appelle **SQLInstallTranslator** via une application ODBC *3.x* pilote, le Gestionnaire de pilotes mappe l’appel à  **SQLInstallTranslatorEx**. Une application ne doit pas appeler **SQLInstallTranslator** dans ODBC *3.x* Gestionnaire de pilotes avec les *lpszInfFile* argument défini sur une valeur autre que NULL. ODBC. Fichier INF utilisé dans ODBC *2.x* n’est plus pris en charge dans ODBC *3.x*, même pour la compatibilité descendante.
