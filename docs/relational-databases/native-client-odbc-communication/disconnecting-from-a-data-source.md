---
title: Déconnexion d’une source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5a7cb061c308508b0ab5d489dcabb4b25f93883
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784752"
---
# <a name="disconnecting-from-a-data-source"></a>Déconnexion d'une source de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lorsqu’une application a fini d’utiliser une source de données, elle appelle **SQLDisconnect**. **SQLDisconnect** libère toutes les instructions qui sont allouées sur la connexion et déconnecte le pilote de la source de données. Après la déconnexion, l’application peut appeler [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) pour libérer le handle de connexion. Avant de quitter, une application appelle également **SQLFreeHandle** pour libérer le handle d’environnement.  
  
 Après la déconnexion, une application peut réutiliser le handle de connexion alloué, se connecter à une autre source de données ou se reconnecter à la même source de données. La décision de rester connecté au lieu de se déconnecter et de se reconnecter ultérieurement requiert que le writer d'application considère les coûts relatifs de chaque option. La connexion à une source de données et le fait de demeurer connecté peut être relativement coûteux, selon le moyen de connexion. En faisant un compromis, l'application doit aussi faire des hypothèses sur la probabilité et le minutage d'opérations supplémentaires sur la même source de données. Une application peut devoir utiliser également plusieurs connexions.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
