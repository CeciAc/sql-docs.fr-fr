---
title: Méthode setCursorName (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setCursorName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3f3ec4f2-103a-4e16-9206-c5bd8639f946
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3f743ddb27b079a4b98d5e00c8ab378a5a6859a1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974506"
---
# <a name="setcursorname-method-sqlserverstatement"></a>Méthode setCursorName (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de curseur SQL selon la chaîne donnée, qui est exécutée par les méthodes d'exécution suivantes.  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. L'appel de cette méthode est sans effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setCursorName(java.lang.String name)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom*  
  
 **Chaîne** qui contient le nom du curseur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCursorName est spécifiée par la méthode setCursorName dans l’interface java. Sql. Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
