---
title: NON NULL dans les instructions CREATE TABLE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4147e560d953b97ecba2e707d354bb6bf2ead59b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834827"
---
# <a name="not-null-in-create-table-statements"></a>NOT NULL dans les instructions CREATE TABLE
Certaines bases de données et en particulier de bureau, ne prennent pas en charge la **pas NULL** contrainte de colonne dans **CREATE TABLE** instructions. Pour plus d’informations, consultez l’option SQL_NON_NULLABLE_COLUMNS dans le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.
