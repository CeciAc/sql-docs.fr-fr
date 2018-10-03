---
title: GetBytes, méthode (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6e88cea-54b3-4d18-a9af-db54abf19f45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1369c40e071d6045bdf42b6c425fb4b94932cf08
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655579"
---
# <a name="getbytes-method-sqlservercallablestatement"></a>Méthode getBytes (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que tableau d'octets.  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Nom   |Description|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int.md)|Récupère la valeur du paramètre désigné en tant que valeur de tableau d'octets en fonction de l'index de paramètre.|  
|[getBytes (java.lang.String)](../../../connect/jdbc/reference/getbytes-method-java-lang-string.md)|Récupère la valeur du paramètre désigné en tant que valeur de tableau d'octets en fonction du nom du paramètre.|  
  
## <a name="remarks"></a>Notes   
 Dans la version précédente du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerCallableStatement.getBytes pour convertir des valeurs entre des tableaux d’octets et le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
