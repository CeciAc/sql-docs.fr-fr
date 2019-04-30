---
title: Sqlsetscrolloptions, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetScrollOptions
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5520554b509b0c25d62e4a191e16ad3524a02652
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63297461"
---
# <a name="sqlsetscrolloptions-mapping"></a>SQLSetScrollOptions, mappage
Lorsqu’une application appelle **SQLSetScrollOptions** via un ODBC 3 *.x* pilote et le pilote ne prend pas en charge **SQLSetScrollOptions**, l’appel à  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 entraîne comme suit :  
  
-   Un appel à  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     avec le *InfoType* affectée à une des valeurs dans le tableau suivant, selon la valeur de l’argument le *KeysetSize* argument dans **SQLSetScrollOptions**.  
  
    |*Argument de KeysetSize*|*InfoType argument*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Une valeur supérieure à la *la RowsetSize* argument|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Si la valeur de la *KeysetSize* argument n’est pas répertorié dans le tableau précédent, l’appel à **SQLSetScrollOptions** retourne SQLSTATE S1107 (ligne valeur hors limites) et aucune des étapes suivantes effectuée.  
  
     Le Gestionnaire de pilotes, puis vérifie si le bit correspondant est défini le **InfoValuePtr* valeur retournée par l’appel à **SQLGetInfo**, en fonction de la valeur de la *l’accèsconcurrentiel* argument dans **SQLSetScrollOptions**.  
  
    |*Accès concurrentiel* argument|*InfoType* paramètre|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Si le *concurrence* argument n’est pas une des valeurs dans le tableau précédent, l’appel à **SQLSetScrollOptions** retourne SQLSTATE S1108 (option de concurrence hors limites) et aucune des étapes suivantes effectuée. Si le bit approprié (comme indiqué dans le tableau précédent) n’est pas défini dans **InfoValuePtr* à une des valeurs correspondant à la *concurrence* argument, l’appel à  **SQLSetScrollOptions** retourne SQLSTATE S1C00 (non compatibles avec le pilote) et aucune des étapes suivantes sont effectuées.  
  
-   Un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     avec  *\*ValuePtr* défini sur l’une des valeurs dans le tableau suivant, en fonction de la valeur de la *KeysetSize* argument dans **SQLSetScrollOptions**.  
  
    |*KeysetSize* argument|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Une valeur supérieure à la *la RowsetSize* argument|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     avec  *\*ValuePtr* défini sur le *concurrence* argument dans **SQLSetScrollOptions**.  
  
-   Si le *KeysetSize* argument dans l’appel à **SQLSetScrollOptions** est un nombre positif, un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     avec  *\*ValuePtr* défini sur le *KeysetSize* argument dans **SQLSetScrollOptions**.  
  
-   Un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     avec  *\*ValuePtr* défini sur le *la RowsetSize* argument dans **SQLSetScrollOptions**.  
  
    > [!NOTE]  
    >  Lorsque le Gestionnaire de pilotes mappe **SQLSetScrollOptions** pour une application qui fonctionne avec un ODBC 3 *.x* pilote qui ne prend pas en charge **SQLSetScrollOptions**, le pilote Le gestionnaire définit l’option d’instruction SQL_ROWSET_SIZE, pas l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE, à la *la RowsetSize* argument dans **SQLSetScrollOption**. Par conséquent, **SQLSetScrollOptions** ne peut pas être utilisé par une application lors de l’extraction de plusieurs lignes par un appel à **SQLFetch** ou **SQLFetchScroll**. Il peut être uniquement utilisé lorsque l’extraction de plusieurs lignes par un appel à **SQLExtendedFetch**.
