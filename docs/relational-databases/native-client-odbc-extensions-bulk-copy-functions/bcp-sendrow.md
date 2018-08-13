---
title: bcp_sendrow | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 937ea3a4086e65712f77b569976902fbd2038007
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561909"
---
# <a name="bcpsendrow"></a>bcp_sendrow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Envoie une ligne de données à partir de variables de programme à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Le **bcp_sendrow** fonction génère une ligne à partir de variables de programme et l’envoie à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Avant d’appeler **bcp_sendrow**, vous devez effectuer les appels à [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) pour spécifier les variables de programme contenant les données de ligne.  
  
 Si **bcp_bind** est appelé en spécifiant un type de données long, de longueur variable, par exemple, un *eDataType* paramètre SQLTEXT et une valeur non NULL *pData* paramètre, **bcp_sendrow** envoie la valeur de données entière, comme il le fait pour tout autre type de données. If, toutefois, **bcp_bind** a une valeur NULL *pData* paramètre, **bcp_sendrow** retourne le contrôle à l’application immédiatement après que toutes les colonnes avec des données spécifiées sont envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’application peut ensuite appeler [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) à plusieurs reprises pour envoyer les données longues de longueur variable à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un segment à la fois. Pour plus d’informations, consultez [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Lorsque **bcp_sendrow** sert à en bloc des lignes de copie à partir de variables de programme dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, les lignes sont validées uniquement lorsque l’utilisateur appelle [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) ou [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) . L'utilisateur peut choisir d'appeler **bcp_batch** une fois chaque *n* lignes ou lors de creux entre deux périodes de données entrantes. Si **bcp_batch** n'est jamais appelé, les lignes sont validées lorsque **bcp_done** est appelé.  
  
 Pour plus d’informations sur les importantes modifier une copie en bloc de début dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], consultez [effectuant des opérations de copie en bloc &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
