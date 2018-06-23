---
title: Pour plus d’informations dans les Interfaces d’erreur | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f6259d21a8b538742509b6f17efedc6530d5e60c
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35699130"
---
# <a name="information-in-error-interfaces"></a>Informations dans les interfaces d'erreur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client signale certaines informations d’erreur et d’état dans les interfaces d’erreur défini par OLE DB **IErrorInfo**, **IErrorRecords**, et **ISQLErrorInfo** .  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client **IErrorInfo** membre fonctionne comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetDescription**|Chaîne du message d'erreur descriptive.|  
|**GetGUID**|GUID de l'interface ayant défini l'erreur.|  
|**GetHelpContext**|Non pris en charge. Retourne toujours zéro.|  
|**GetHelpFile**|Non pris en charge. Retourne toujours la valeur Null.|  
|**GetSource**|Chaîne « Microsoft SQL Server Native Client ».|  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge disponibles de consommateur **IErrorRecords** membre fonctionne comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Remplit une structure ERRORINFO avec des informations de base sur une erreur. Une structure ERRORINFO contient des membres qui identifient la valeur de retour HRESULT pour l'erreur, ainsi que le fournisseur et l'interface auxquels l'erreur s'applique.|  
|**GetCustomErrorObject**|Retourne une référence sur les interfaces **ISQLErrorInfo,** et [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Retourne une référence à un **IErrorInfo** interface.|  
|**GetErrorParameters**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ne retourne pas de paramètres au consommateur via **GetErrorParameters**.|  
|**GetRecordCount**|Nombre d'enregistrements d'erreur disponibles.|  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client **ISQLErrorInfo::GetSQLInfo** paramètres comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Retourne une valeur SQLSTATE pour l'erreur. Les valeurs SQLSTATE sont définies dans les spécifications SQL-92, ODBC et ISO SQL, et API. Ni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ni le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif défini par les valeurs SQLSTATE spécifiques à l’implémentation.|  
|*plNativeError*|Retourne le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] numéro d’erreur de **master.dbo.sysmessages** lorsqu’il est disponible. Erreurs natives sont disponibles après une tentative d’initialiser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données du fournisseur OLE DB Native Client. Avant la tentative, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif retourne toujours zéro.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
