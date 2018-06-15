---
title: Transactions | Documents Microsoft
description: Transactions dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: fecf4c91b95cdb140261afe5303520d11d63afe7
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308298"
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server implémente la prise en charge de la transaction locale. Le consommateur peut utiliser des transactions distribuées ou coordonnées à l'aide de Microsoft Distributed Transaction Coordinator (MS DTC). Pour les consommateurs nécessiter le contrôle de transaction qui s’étend sur plusieurs sessions, le pilote OLE DB pour SQL Server peut joindre des transactions lancées et gérées par MS DTC.  
  
 Par défaut, le pilote OLE DB pour SQL Server utilise un mode de transaction de validation automatique, où chaque action discrète dans une session de consommateur comprend une transaction complète sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le pilote OLE DB pour le mode de validation automatique de SQL Server est local, et les transactions validées automatiquement ne couvrent jamais plus d’une session.  
  
 Le pilote OLE DB pour SQL Server expose la **ITransactionLocal** interface, ce qui permet au consommateur d’utiliser explicitement et implicitement démarrer des transactions sur une seule connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le pilote OLE DB pour SQL Server ne prend pas en charge les transactions locales imbriquées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prise en charge des transactions locales](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Prise en charge des transactions distribuées](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Niveaux d’isolation &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
