---
title: Obtention de descripteur gère | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 983097de95e41914bb4d577cb071d790a795f96d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853947"
---
# <a name="obtaining-descriptor-handles"></a>Obtention des handles de descripteur
Une application obtient le handle de descripteur alloué explicitement comme un argument de sortie de l’appel à **SQLAllocHandle**. Le handle d’un descripteur alloué implicitement est obtenu en appelant **SQLGetStmtAttr**.
