---
title: Méthode updateClob (int, Java. IO. Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: df60fbf1-44b2-4658-84a5-5cb129ce2dc6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4aebc496766fbf8358e7e18004cd74779cbbfafa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996638"
---
# <a name="updateclob-method-int-javaioreader"></a>Méthode updateClob (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée à l'aide de l'objet Reader spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateClob(int columnIndex,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 **Entier** qui indique l’index de colonne.  
  
 *reader*  
  
 Objet lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateClob est spécifiée par la méthode updateClob de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
