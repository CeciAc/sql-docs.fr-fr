---
title: IsClosed, méthode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbd0e8ce34d14f0ef9fa77f3c2f64cc4e5804fb5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718327"
---
# <a name="isclosed-method-sqlserverstatement"></a>Méthode isClosed (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) a été fermé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet est fermé, **false** si elle est toujours ouverte.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode isClosed est spécifiée par la méthode isClosed dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
