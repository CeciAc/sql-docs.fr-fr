---
title: Pour plus d’informations dans les Interfaces d’erreur | Documents Microsoft
description: Pour plus d’informations dans les interfaces d’erreur
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 514b2328fce0f400315be4d21539f766f8715890
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666139"
---
# <a name="information-in-error-interfaces"></a>Informations dans les interfaces d'erreur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server signale des informations d’erreur et d’état dans les interfaces d’erreur défini par OLE DB **IErrorInfo**, **IErrorRecords**, et **ISQLErrorInfo**.  
  
 Le pilote OLE DB pour SQL Server prend en charge **IErrorInfo** membre fonctionne comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetDescription**|Chaîne du message d'erreur descriptive.|  
|**GetGUID**|GUID de l'interface ayant défini l'erreur.|  
|**GetHelpContext**|Non pris en charge. Retourne toujours zéro.|  
|**GetHelpFile**|Non pris en charge. Retourne toujours la valeur Null.|  
|**GetSource**|Chaîne « Microsoft OLE DB Driver pour SQL Server ».|  
  
 Le pilote OLE DB pour SQL Server prend en charge disponibles de consommateur **IErrorRecords** membre fonctionne comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Remplit une structure ERRORINFO avec des informations de base sur une erreur. Une structure ERRORINFO contient des membres qui identifient la valeur de retour HRESULT pour l'erreur, ainsi que le fournisseur et l'interface auxquels l'erreur s'applique.|  
|**GetCustomErrorObject**|Retourne une référence sur les interfaces **ISQLErrorInfo,** et [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Retourne une référence à un **IErrorInfo** interface.|  
|**GetErrorParameters**|Le pilote OLE DB pour SQL Server ne retourne pas de paramètres au consommateur via **GetErrorParameters**.|  
|**GetRecordCount**|Nombre d'enregistrements d'erreur disponibles.|  
  
 Le pilote OLE DB pour SQL Server prend en charge **ISQLErrorInfo::GetSQLInfo** paramètres comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Retourne une valeur SQLSTATE pour l'erreur. Les valeurs SQLSTATE sont définies dans les spécifications SQL-92, ODBC et ISO SQL, et API. Ni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ni le pilote OLE DB pour SQL Server définie par les valeurs SQLSTATE spécifiques à l’implémentation.|  
|*plNativeError*|Retourne le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] numéro d’erreur de **master.dbo.sysmessages** lorsqu’il est disponible. Erreurs natives sont disponibles après une tentative d’initialisation d’un pilote OLE DB pour la source de données SQL Server. Avant la tentative, le pilote OLE DB pour SQL Server retourne toujours zéro.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)  
  
  
