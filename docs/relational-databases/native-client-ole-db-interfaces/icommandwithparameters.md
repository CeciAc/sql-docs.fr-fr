---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 463cf745cc31f65833fd8f58fda95ae13362be62
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73763184"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les améliorations apportées au moteur de base de données à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] autorisent ICommandWithParameters :: GetParameterInfo à obtenir des descriptions plus précises des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par CommandWithParameters :: GetParameterInfo dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], lors de l’appel d’ICommandWithParameters::SetParameterInfo, la valeur passée au paramètre *pwszName* doit être un identificateur valide. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
