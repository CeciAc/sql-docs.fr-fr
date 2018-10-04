---
title: DLL de traduction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1d0e23019f3e5b68ad38711c1f041b160ceb31
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833857"
---
# <a name="translation-dlls"></a>DLL de translation
L’application et la source de données stockent souvent des données dans plusieurs jeux de caractères. ODBC fournit un mécanisme générique qui permet au pilote de convertir les données d’un jeu de caractères à un autre. Il se compose d’une DLL qui implémente les fonctions de traduction **SQLDriverToDataSource** et **SQLDataSourceToDriver**, qui sont appelés par le pilote à traduire toutes les données qui circulent entre la source de données et le pilote. Cette DLL peut être écrit par le développeur d’applications, le développeur de pilote, ou un tiers.  
  
 La DLL de traduction pour une source de données particulier peut être spécifiée dans les informations système pour cette source de données ; Pour plus d’informations, consultez [sous-clés de spécification de Source de données](../../../odbc/reference/install/data-source-specification-subkeys.md). Elle peut également être définie au moment de l’exécution avec les attributs de connexion SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION.  
  
 L’option de traduction est une valeur qui peut être interprétée uniquement par une DLL de traduction spécifique. Par exemple, si la traduction DLL traduit entre différentes pages de codes, l’option peut donner les numéros des pages de code utilisées par l’application et la source de données. Il n’est pas obligé d’utiliser une option de traduction pour une DLL de traduction.  
  
 Après une traduction que DLL a été spécifié, le pilote charge et appelle pour convertir toutes les données transitant entre l’application et la source de données. Cela inclut toutes les instructions SQL et les paramètres de caractères envoyés à la source de données, et tous les résultats de caractère, les métadonnées de caractères tels que les noms de colonnes et les messages d’erreur récupérées à partir de la source de données. Données de connexion ne sont pas traduites, étant donné que la DLL de traduction n’est pas chargée tant qu’après que l’application est connectée à la source de données.
