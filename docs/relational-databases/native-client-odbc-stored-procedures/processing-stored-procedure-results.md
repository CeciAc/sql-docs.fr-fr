---
title: Traitement des résultats de la procédure stockée | Microsoft Docs
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
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 588316b5fd9cc3fa9f5cc5dc2ecefadb3ae248ef
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43060522"
---
# <a name="processing-stored-procedure-results"></a>Traitement des résultats des procédures stockées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent quatre mécanismes pour retourner les données :  
  
-   Chaque instruction SELECT de la procédure génère un jeu de résultats.  
  
-   La procédure peut retourner des données par l'intermédiaire de paramètres de sortie.  
  
-   Un paramètre de sortie de curseur peut retourner un curseur côté serveur [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   La procédure peut avoir un code de retour de type entier.  
  
 Les applications doivent être en mesure de gérer toutes les sorties provenant des procédures stockées. L'instruction CALL ou EXECUTE doit inclure des marqueurs de paramètre pour le code de retour et les paramètres de sortie. Utilisez [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) à tous les lier comme paramètres de sortie et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client transfère les valeurs de sortie dans les variables liées. Paramètres de sortie et codes de retour sont les derniers éléments retournés au client par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; ils ne sont pas retournés à l’application tant que [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) retourne SQL_NO_DATA.  
  
 ODBC ne prend pas en charge la liaison des paramètres [!INCLUDE[tsql](../../includes/tsql-md.md)] de type cursor. Comme tous les paramètres de sortie doivent être liés avant d'exécuter une procédure, toute procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] qui contient un paramètre de curseur de sortie ne peut pas être appelée par les applications ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
