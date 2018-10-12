---
title: Méthode setDate setDate (méthode) à la valeur de date - chaîne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setDate (java.lang.String, java.sql.Date)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4762e2bd-5e94-4562-97d5-f023ecffc08c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da5eedcbdd76e16da87f8e84c35fa07ef2cc5ccc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683537"
---
# <a name="setdate-method-javalangstring-javasqldate"></a>Méthode setDate (java.lang.String, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur de date donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setDate(java.lang.String sCol,  
                    java.sql.Date d)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *d*  
  
 Un objet Date.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setDate est spécifiée par la méthode setDate de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
