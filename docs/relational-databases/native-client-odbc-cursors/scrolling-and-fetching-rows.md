---
title: Défilement et extraction des lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5b45e71e5501a1c294760c4e7cadba5f96b169e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078811"
---
# <a name="scrolling-and-fetching-rows"></a>Défilement et extraction de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Pour utiliser un curseur permettant le défilement, une application ODBC doit :  
  
-   Définissez les fonctionnalités de curseur à l’aide de [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Ouvrez le curseur à l’aide **SQLExecute** ou **SQLExecDirect**.  
  
-   Faire défiler et extraire des lignes à l’aide **SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Les deux **SQLFetch** et **SQLFetchScroll** peut extraire des blocs de lignes à la fois. Le nombre de lignes retourné est spécifié à l’aide de **SQLSetStmtAttr** pour définir le paramètre SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Les applications ODBC peuvent utiliser **SQLFetch** pour extraire un curseur avant uniquement.  
  
 **SQLFetchScroll** est utilisé pour faire défiler un curseur. **SQLFetchScroll** prend en charge l’extraction de la suivante, précédente, première et dernière ensembles de lignes en plus de l’extraction relative (extraire l’ensemble de lignes *n* lignes à partir du début de l’ensemble de lignes actuel) et absolu extraction (fetch l’ensemble de lignes en commençant à la ligne *n*). Si *n* est négatif dans une extraction absolue, les lignes sont comptées à partir de la fin du jeu de résultats. Une extraction absolue de ligne -1 équivaut à l'extraction de l'ensemble de lignes qui démarre à la dernière ligne du jeu de résultats.  
  
 Les applications qui utilisent **SQLFetchScroll** uniquement pour son bloc fonctionnalités du curseur, tels que des rapports, sont susceptibles de passer par le jeu de résultats une seule fois, à l’aide de l’option uniquement pour extraire l’ensemble de lignes suivant. Applications basées sur l’écran, quant à eux, peuvent tirer parti de toutes les fonctionnalités de **SQLFetchScroll**. Si l’application définit la taille de l’ensemble de lignes sur le nombre de lignes affichées sur l’écran et lie les mémoires tampons d’écran au jeu de résultats, il peut traduire directement aux appels à des opérations de barre de défilement **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Pg. suiv|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec FetchOffset égal à -1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec FetchOffset égal à 1|  
|Case de défilement vers le haut|SQL_FETCH_FIRST|  
|Case de défilement vers le bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de signets pour des lignes dans ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de curseurs &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
