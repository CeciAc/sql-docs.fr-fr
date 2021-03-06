---
title: getDouble, méthode (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDouble (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c0ed63bb-5ebe-4155-9f91-8fbfeac9c3b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b02292225d0f0be0529537f369c2fa760d677486
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983595"
---
# <a name="getdouble-method-int"></a>Méthode getDouble (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné sous forme d’objet **double** dans le langage de programmation Java en fonction de l’index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public double getDouble(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **Entier** qui indique l’index du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur de **type double** .  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getDouble est spécifiée par la méthode getDouble de l’interface java.sql.CallableStatement.  
  
 Cette méthode retourne tous les types de données numériques avec la fidélité **double** Java.  
  
## <a name="see-also"></a>Voir aussi  
 [getDouble, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
