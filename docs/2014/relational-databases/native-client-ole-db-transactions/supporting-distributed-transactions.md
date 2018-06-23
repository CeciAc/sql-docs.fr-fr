---
title: Prise en charge des Transactions distribuées | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bae96ffb9b49aead4282193c510a50098d0e0d54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041106"
---
# <a name="supporting-distributed-transactions"></a>Prise en charge des Transactions distribuées
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consommateurs du fournisseur OLE DB du Client natifs peuvent utiliser le **ITransactionJoin::JoinTransaction** méthode devant être inclus dans une transaction distribuée coordonnée par Microsoft Distributed Transaction Coordinator (MS DTC).  
  
 MS DTC expose les objets COM qui permettent aux clients d'initialiser des transactions coordonnées et d'y participer sur plusieurs connexions à diverses banques de données. Pour lancer une transaction, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client utilise MS DTC **ITransactionDispenser** interface. Le **BeginTransaction** membre **ITransactionDispenser** retourne une référence à un objet de transaction distribuée. Cette référence est passée à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client à l’aide de **JoinTransaction**.  
  
 MS DTC prend en charge l'abandon et la validation asynchrones sur les transactions distribuées. Pour la notification sur l’état de transaction asynchrone, le consommateur implémente la **ITransactionOutcomeEvents** interface et connecte l’interface à un objet de transaction MS DTC.  
  
 Pour les transactions distribuées, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implémente du fournisseur OLE DB Native Client **ITransactionJoin::JoinTransaction** paramètres comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*punkTransactionCoord*|Pointeur vers un objet de transaction MS DTC.|  
|*IsoLevel*|Ignoré par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Le niveau d'isolation pour les transactions coordonnées MS DTC est déterminé lorsque le consommateur acquiert un objet de transaction à partir de MS DTC.|  
|*Indicateur IsoFlags*|Doit être égal à 0. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne XACT_E_NOISORETAIN si toute autre valeur est spécifiée par le consommateur.|  
|*POtherOptions*|Si non NULL, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client demande à l’objet d’options de l’interface. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne XACT_E_NOTIMEOUT si l’objet d’options *ulTimeout* membre n’est pas zéro. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ignore la valeur de la *szDescription* membre.|  
  
 Cet exemple coordonne la transaction à l'aide de MS DTC.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](transactions.md)  
  
  