---
title: Méthode getServerName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 487d214dbdd6974442749dd0cff6ac24fe9d1977
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979955"
---
# <a name="getservername-method-sqlserverdatasource"></a>Méthode getServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom de l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **Chaîne** qui contient le nom du serveur ou null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Le nom du serveur correspond au nom d’hôte de l’ordinateur cible qui exécute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété getServerName n’est pas définie, getServerName retourne la valeur par défaut, qui est Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
