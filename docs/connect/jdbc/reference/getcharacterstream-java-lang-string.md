---
title: getCharacterStream (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getCharacterStream(String paramName)
apilocation:
- SQLServerCallableStatement.getCharacterStream(String paramName)
apitype: Assembly
ms.assetid: 5281e1b8-19b8-4fe5-83be-929d1987e25d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e52ff3e9bc9da36d3874382341a1f46eb722ad3c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953546"
---
# <a name="getcharacterstream-javalangstring"></a>getCharacterStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu'objet java.io.Reader en fonction du nom du paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.io.Reader getCharacterStream(java.lang.String paramName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *paramName*  
  
 **Chaîne** qui indique le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getCharacterStream, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
