---
title: PDO::ErrorCode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73bc57c0519c3371b77e38b00b7cc2a8a203b811
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37999189"
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode récupère la valeur SQLSTATE de la dernière opération sur le handle de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>Valeur retournée  
PDO::errorCode retourne une valeur SQLSTATE à cinq caractères sous la forme d’une chaîne, ou NULL si aucune opération n’a eu lieu sur le handle de base de données.  
  
## <a name="remarks"></a>Notes   
PDO::errorCode dans le pilote PDO_SQLSRV retourne des avertissements sur certaines opérations réussies. Par exemple, sur une connexion réussie, PDO::errorCode retourne 01000, ce qui indique SQL_SUCCESS_WITH_INFO.  
  
PDO::errorCode récupère uniquement les codes d’erreur des opérations exécutées directement sur la connexion de base de données. Si vous créez une instance PDOStatement par le biais de PDO::prepare ou PDO::query et qu’une erreur est générée sur l’objet d’instruction, PDO::errorCode ne récupère pas cette erreur. Vous devez appeler PDOStatement::errorCode pour retourner le code d’erreur d’une opération effectuée sur un objet d’instruction particulier.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a> Exemple  
Dans cet exemple, le nom de la colonne est mal orthographié (`Cityx` au lieu de `City`), ce qui provoque une erreur qui est ensuite signalée.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a> Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
