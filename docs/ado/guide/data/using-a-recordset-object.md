---
title: À l’aide d’un objet Recordset | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 01c630d8-eb35-4bd0-a99f-7c0f85316cc1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05a2c989d1f14849ef39b4ec93f4677ebc52510e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273178"
---
# <a name="using-a-recordset-object"></a>À l’aide d’un objet Recordset
Vous pouvez également utiliser **Recordset.Open** pour établir une connexion implicitement et d’émettre une commande sur la connexion en une seule opération. Par exemple, dans Visual Basic :  
  
```  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.CursorLocation = adUseClient  
oRs.Open sSQL, sConn, adOpenStatic, _  
               adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
oRs.Close          
Set oRs = Nothing  
```  
  
 Notez que **oRs.Open** prend une chaîne de connexion (*sConn*), au lieu d’un **connexion** objet (*oConn*), comme la valeur de son  **ActiveConnection** paramètre. Également le type de curseur côté client est appliqué en définissant le **CursorLocation** propriété sur le **Recordset** objet. Là encore, Ceci contraste avec le **HelloData** exemple.
