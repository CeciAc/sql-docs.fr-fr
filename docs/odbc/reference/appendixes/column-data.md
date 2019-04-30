---
title: Données de la colonne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95f80c82d3804e31d5ea29d55af0fbedd4184e6c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213848"
---
# <a name="column-data"></a>Données de la colonne
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs crée une mémoire tampon dans le cache pour chaque tampon de données lié à un jeu de résultats avec **SQLBindCol**. Il utilise les valeurs de ces mémoires tampons pour construire un **où** clause lorsqu’il émule un positionnées mettre à jour ou supprimer l’instruction. Il met à jour ces mémoires tampons à partir de mémoires tampons de l’ensemble de lignes lorsqu’il extrait des données à partir de la source de données et lorsqu’il s’exécute les instructions de mise à jour positionnée.  
  
 Lorsque la bibliothèque de curseurs met à jour son cache de mémoires tampons de l’ensemble de lignes, il transfère les données en fonction du type de données C spécifiée dans **SQLBindCol**. Par exemple, si le type de données C d’une mémoire tampon d’ensemble de lignes est SQL_C_SLONG, la bibliothèque de curseurs transfère les quatre octets de données ; s’il s’agit SQL_C_CHAR et *BufferLength* est 10, la bibliothèque de curseurs transfère 10 octets de données. La bibliothèque de curseurs n’effectue pas la vérification de type ni conversions sur les données que du transfert.  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne met pas à jour son cache pour une colonne si **StrLen_or_IndPtr* dans l’ensemble de lignes correspondante mémoire tampon est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC.  
  
 Quand il met à jour une colonne, une source vide-panneaux caractères de longueur fixe de données et les données binaires de longueur fixe de panneaux de zéro si nécessaire. Par exemple, une source de données stocke « Smith » dans une colonne char (10) en tant que « Smith ». La bibliothèque de curseurs ne pas blancs ou zéro-remplissage des données dans les mémoires tampons d’ensemble de lignes lorsqu’il copie ces données à son cache après l’exécution d’une instruction de mise à jour positionnée. Par conséquent, si une application nécessite que les valeurs dans le cache de la bibliothèque de curseurs sont complétées par des blancs ou de zéros, elle doit être blancs ou zéro-panneau les valeurs dans les mémoires tampons d’ensemble de lignes avant d’exécuter une instruction de mise à jour positionnée.
