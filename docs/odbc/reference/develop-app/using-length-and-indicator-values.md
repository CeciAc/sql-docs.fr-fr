---
title: À l’aide de la longueur et les valeurs d’indicateur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- length/indicator buffers [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 442d0865ede4819ea3413d662411295daa5b48bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646017"
---
# <a name="using-length-and-indicator-values"></a>Utilisation des valeurs de longueur et d’indicateur
La mémoire tampon de longueur / d’indicateur est utilisée pour passer la longueur d’octet des données dans le tampon de données ou un indicateur spécial tel que SQL_NULL_DATA, ce qui indique que les données sont NULL. En fonction de la fonction dans laquelle il est utilisé, une mémoire tampon de longueur / d’indicateur est définie comme un SQLINTEGER ou un SQLSMALLINT. Par conséquent, un seul argument est nécessaire pour le décrire. Si la mémoire tampon de données est une mémoire tampon d’entrée nondeferred, cet argument contient la longueur d’octet des données elles-mêmes ou une valeur d’indicateur. Il est souvent nommé *StrLen_or_Ind* ou un nom similaire. Par exemple, ce qui suit code appelle **SQLPutData** à passer une mémoire tampon complète de données ; la longueur d’octet (*ValueLen*) est passée directement, car le tampon de données (*ValuePtr*) est un mémoire tampon d’entrée.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLen;  
  
// Call local function to place data in ValuePtr. In ValueLen, return the  
// number of bytes of data placed in ValuePtr. If there is not enough  
// data, this will be less than 50.  
FillBuffer(ValuePtr, sizeof(ValuePtr), &ValueLen);  
  
// Call SQLPutData to send the data to the driver.  
SQLPutData(hstmt, ValuePtr, ValueLen);  
```  
  
 Si la mémoire tampon de données est une mémoire tampon d’entrée différé, une mémoire tampon de sortie nondeferred ou un mémoire tampon de sortie, l’argument contient l’adresse de la mémoire tampon de longueur / d’indicateur. Il est souvent nommé *StrLen_or_IndPtr* ou un nom similaire. Par exemple, ce qui suit code appelle **SQLGetData** pour récupérer une mémoire tampon complète des données ; la longueur d’octet est retournée à l’application dans la mémoire tampon de longueur / d’indicateur (*ValueLenOrInd*), dont l’adresse est passé à **SQLGetData** , car la mémoire tampon de données correspondante (*ValuePtr*) est une mémoire tampon de sortie nondeferred.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Sauf si elle est spécifiquement interdit, un argument de mémoire tampon de longueur / d’indicateur peut être 0 (si une entrée nondeferred) ou un pointeur null (si output ou input différée). Pour les mémoires tampons d’entrée, cela entraîne le pilote ignorer la longueur d’octet des données. Retourne une erreur lors du passage des données de longueur variable, mais est courant lors du passage des données non null, de longueur fixe, étant donné que ni une longueur ni une valeur de l’indicateur est nécessaire. Pour les mémoires tampons de sortie, cela entraîne le pilote pour ne pas retourner la longueur d’octet des données ou une valeur d’indicateur. Il s’agit d’une erreur si les données retournées par le pilote a la valeur NULL mais qu’il sont courantes lors de la récupération des données de longueur fixe, non nullable, étant donné que ni une longueur ni une valeur de l’indicateur est nécessaire.  
  
 En tant que lorsque l’adresse d’une mémoire tampon de données différée est passée au pilote, l’adresse d’une mémoire tampon de longueur / d’indicateur différée doit rester valide jusqu'à ce que la mémoire tampon est indépendante.  
  
 Les longueurs suivantes sont valides en tant que valeurs de longueur / d’indicateur :  
  
-   *n*, où *n* > 0.  
  
-   0.  
  
-   SQL_NTS. Une chaîne envoyée au pilote dans la mémoire tampon de données correspondante est terminée ; Il s’agit d’un moyen pratique pour les programmeurs C passer des chaînes sans avoir à calculer leur longueur en octets. Cette valeur est autorisée uniquement lorsque l’application envoie des données au pilote. Lorsque le pilote retourne des données à l’application, elle retourne toujours la longueur d’octet réelle des données.  
  
 Les valeurs suivantes sont valides en tant que valeurs de longueur / d’indicateur. SQL_NULL_DATA est stocké dans le champ de descripteur SQL_DESC_INDICATOR_PTR ; toutes les autres valeurs sont stockées dans le champ de descripteur SQL_DESC_OCTET_LENGTH_PTR.  
  
-   SQL_NULL_DATA. Les données sont une valeur NULL, et la valeur dans la mémoire tampon de données correspondante est ignorée. Cette valeur est autorisée uniquement pour les données SQL envoyées à ou à récupérer à partir du pilote.  
  
-   SQL_DATA_AT_EXEC. Le tampon de données ne contient-elle pas de données. Au lieu de cela, les données sont envoyées avec **SQLPutData** lorsque l’instruction est exécutée ou lorsque **SQLBulkOperations** ou **SQLSetPos** est appelée. Cette valeur est autorisée uniquement pour les données SQL envoyées au pilote. Pour plus d’informations, consultez [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), et [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro). Cette valeur est similaire à SQL_DATA_AT_EXEC. Pour plus d’informations, consultez [envoyer les données de type Long](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Le pilote ne peut pas déterminer le nombre d’octets de données de type long toujours disponibles à renvoyer dans un mémoire tampon de sortie. Cette valeur est autorisée uniquement pour les données SQL récupérées à partir du pilote.  
  
-   SQL_DEFAULT_PARAM. Une procédure consiste à utiliser la valeur par défaut d’un paramètre d’entrée dans une procédure au lieu de la valeur dans la mémoire tampon de données correspondante.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** ou **SQLSetPos** consiste à ignorer la valeur dans la mémoire tampon de données. Lors de la mise à jour d’une ligne de données par un appel à **SQLBulkOperations** ou **SQLSetPos,** la valeur de colonne n’est pas modifiée. Lors de l’insertion d’une nouvelle ligne de données par un appel à **SQLBulkOperations**, la valeur de colonne est définie sur sa valeur par défaut ou, si la colonne n’a pas de valeur par défaut, null.
