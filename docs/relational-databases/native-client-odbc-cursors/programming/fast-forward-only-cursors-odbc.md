---
title: Curseurs avant uniquement rapides (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dec321e051cbc692b92d5a9611f95cbd80b7399c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737887"
---
# <a name="fast-forward-only-cursors-odbc"></a>Curseurs avant uniquement rapides (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Lors de la connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge les optimisations des performances pour les curseurs avant uniquement et en lecture seule. Les curseurs avant uniquement rapides sont implémentés en interne par le pilote et le serveur d'une manière très semblable aux jeux de résultats par défaut. Les curseurs avant uniquement rapides présentent d'autres caractéristiques, au-delà de leurs performances élevées :  
  
-   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) n’est pas pris en charge. Les colonnes de jeu de résultats doivent être liées à des variables de programme.  
  
-   Le serveur ferme automatiquement le curseur lorsque la fin de celui-ci est détectée. L’application doit toujours appeler [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) ou [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), mais le pilote n’a pas envoyer la demande de fermeture au serveur. Cela permet d'économiser un aller-retour au serveur par le biais du réseau.  
  
 L'application demande des curseurs avant uniquement rapides à l'aide de l'attribut d'instruction SQL_SOPT_SS_CURSOR_OPTIONS spécifique au pilote. Lorsqu'ils sont définis avec la valeur SQL_CO_FFO, les curseurs avant uniquement rapides sont activés sans auto-extraction. Lorsqu'ils sont définis sur SQL_CO_FFO_AF, l'option d'auto-extraction est également activée. Pour plus d’informations sur l’auto-extraction, consultez [à l’aide de l’auto-extraction avec les curseurs ODBC](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md).  
  
 Les curseurs avant uniquement rapides avec auto-extraction peuvent être utilisés pour extraire un petit jeu de résultats avec un seul aller-retour au serveur. Dans ces étapes, *n* est le nombre de lignes à retourner :  
  
1.  Affectez la valeur SQL_CO_FFO_AF à SQL_SOPT_SS_CURSOR_OPTIONS.  
  
2.  Définissez SQL_ATTR_ROW_ARRAY_SIZE sur *n* + 1.  
  
3.  Lier les colonnes de résultats aux tableaux de *n* + 1 éléments (pour plus de sécurité si *n* + 1 lignes seraient extraites).  
  
4.  Ouvrez le curseur avec **SQLExecDirect** ou **SQLExecute**.  
  
5.  Si l’état de retour est SQL_SUCCESS, puis appelez **SQLFreeStmt** ou **SQLCloseCursor** pour fermer le curseur. Toutes les données des lignes seront dans les variables de programme liées.  
  
 Avec ces étapes, le **SQLExecDirect** ou **SQLExecute** envoie une demande d’ouverture de curseur avec l’option d’auto-extraction est activée. Lors de cette demande unique de la part du client, le serveur :  
  
-   ouvre le curseur ;  
  
-   génère le jeu de résultats et envoie les lignes au client ;  
  
-   détecte la fin du curseur et le ferme, la taille de l'ensemble de lignes ayant été définie avec une unité de plus que le nombre de lignes dans le jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseurs &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
