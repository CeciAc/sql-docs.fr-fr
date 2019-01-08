---
title: SQLDriverConnect | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 23475a80aeb63f0681977f096e18886c426c4862
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591254"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit des attributs de connexion qui remplacent ou améliorent les mots clés de chaînes de connexion. Plusieurs mots clés de chaînes de connexion ont des valeurs par défaut définies par le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Pour obtenir la liste de mots clés disponibles dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client, consultez [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attributs de connexion et les comportements par défaut de pilote, consultez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Pour une description des mots clés de chaîne de connexion qui sont valides pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, consultez [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Lorsque le **SQLDriverConnect**_DriverCompletion_ valeur du paramètre est SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client Récupère les valeurs de mot clé à partir de la boîte de dialogue affichée. Si la valeur de mot clé est transmise à la chaîne de connexion et si l'utilisateur ne modifie pas la valeur pour le mot clé dans la boîte de dialogue, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilise la valeur issue de la chaîne de connexion. Si la valeur n'est pas définie dans la chaîne de connexion et si l'utilisateur ne procède à aucune affectation dans la boîte de dialogue, le pilote utilise la valeur par défaut.  
  
 **SQLDriverConnect** doit être donnée valide *WindowHandle* lorsqu’une *DriverCompletion* valeur requiert (ou peut nécessiter) l’affichage de la boîte de dialogue de connexion du pilote. Un handle non valide retourne SQL_ERROR.  
  
 Spécifiez le mot clé DRIVER ou DSN. ODBC indique que, de ces deux mots clés, un pilote utilise celui qui est situé le plus à gauche et ignore l'autre si les deux sont spécifiés. Si le pilote est spécifié, ou est le plus à gauche des deux et le **SQLDriverConnect**_DriverCompletion_ valeur du paramètre est SQL_DRIVER_NOPROMPT, le mot clé SERVER et si une valeur appropriée.  
  
 Lorsque SQL_DRIVER_NOPROMPT est spécifié, les mots clés d'authentification utilisateur doivent être fournis avec des valeurs. Le pilote garantit que la chaîne « Trusted_Connection=yes » ou les mots clés UID et PWD à la fois sont disponibles.  
  
 Si le *DriverCompletion* valeur du paramètre est SQL_DRIVER_NOPROMPT ou SQL_DRIVER_COMPLETE_REQUIRED et la langue ou la base de données provient de la chaîne de connexion et n’est pas valide, **SQLDriverConnect**retourne SQL_ERROR.  
  
 Si le *DriverCompletion* valeur du paramètre est SQL_DRIVER_NOPROMPT ou SQL_DRIVER_COMPLETE_REQUIRED et la langue ou la base de données est fourni à partir des définitions de source de données ODBC et n’est pas valide, **SQLDriverConnect**  utilise la langue par défaut ou la base de données pour l’ID d’utilisateur spécifié et retourne SQL_SUCCESS_WITH_INFO.  
  
 Si le *DriverCompletion* valeur du paramètre est SQL_DRIVER_COMPLETE ou SQL_DRIVER_PROMPT et si la langue ou la base de données est non valide, **SQLDriverConnect** réaffiche la boîte de dialogue.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect prend en charge les fonctionnalités de récupération d'urgence, haute disponibilité  
 Pour plus d’informations sur l’utilisation de **SQLDriverConnect** pour se connecter à un [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] un cluster, consultez [SQL Server Native Client prise en charge pour la haute disponibilité, récupération d’urgence](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Prise en charge de SQLDriverConnect pour les noms de principaux du service (SPN)  
 SQLDDriverConnect utilisera l’activation de l’invite dès boîte de dialogue de connexion ODBC. Celle-ci vous permet d'entrer des SPN à la fois pour le serveur principal et pour le partenaire de basculement.  
  
 SQLDriverConnect acceptera les nouveaux mots clés de chaîne de connexion **ServerSPN** et **FailoverPartnerSPN**et reconnaît les nouveaux attributs de connexion SQL_COPT_SS_SERVER_SPN et SQL_COPT_SS_ FAILOVER_PARTNER_SPN.  
  
 Lorsqu'une valeur d'attribut de connexion est définie plus d'une fois, toute valeur définie par programme à priorité sur la valeur d'un DSN et sur toute valeur dans une chaîne de connexion. Une valeur dans un DSN est prioritaire par rapport à une valeur dans une chaîne de connexion.  
  
 Lors de l'ouverture d'une connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sur la méthode d'authentification employée pour ouvrir la connexion.  
  
 Pour plus d’informations sur les SPN, consultez [noms principaux de Service &#40;SPN&#41; dans les connexions clientes &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Exemples  
 L’appel suivant illustre la moindre quantité de données requises pour **SQLDriverConnect**:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Les chaînes de connexion suivantes illustrent les données minimales requises lorsque la *DriverCompletion* valeur du paramètre est SQL_DRIVER_NOPROMPT :  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLDriverConnect](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [Détails d’implémentation API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
