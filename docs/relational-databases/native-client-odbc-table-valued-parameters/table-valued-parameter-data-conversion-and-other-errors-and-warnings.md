---
title: Les données de paramètre table Conversion et d’autres erreurs et avertissements | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2586866291d348e8e8b59ff8899998c43a2f3a94
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426688"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Conversion des données des paramètres table et autres erreurs et avertissements
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les valeurs de colonne de paramètre table peuvent être converties du type de données client en type de données serveur de la même manière que toute autre valeur de colonne ou de paramètre. Toutefois, dans la mesure où un paramètre table peut contenir plusieurs colonnes et plusieurs lignes, il est important de pouvoir identifier la valeur réelle sur laquelle l'erreur s'est produite.  
  
 Lorsqu'une erreur ou un avertissement est détecté dans une colonne de paramètre table, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client génère un enregistrement de diagnostic. Le message d'erreur contient le numéro du paramètre table, accompagné de l'ordinal de colonne et du numéro de ligne. Une application peut également utiliser les champs de diagnostic SQL_DIAG_SS_TABLE_COLUMN_NUMBER et SQL_DIAG_SS_TABLE_ROW_NUMBER dans des enregistrements de diagnostic pour déterminer quelles valeurs sont associées à des erreurs et des avertissements. Ces champs de diagnostic sont disponibles dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures.  
  
 Les composants SQLSTATE et message des enregistrements de diagnostic sont conformes au comportement ODBC existant pour tous les autres aspects. Autrement dit, mises à part pour les informations d'identification de paramètre, de ligne et de colonne, les messages d'erreur ont les mêmes valeurs pour les paramètres table que pour les paramètres qui ne sont pas des paramètres table.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
