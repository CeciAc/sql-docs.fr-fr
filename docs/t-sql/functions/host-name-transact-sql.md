---
title: HOST_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HOST_NAME_TSQL
- HOST_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- HOST_NAME function
- workstation names [SQL Server]
ms.assetid: 4b8b0705-c083-4b07-b954-c83ee73b2ebb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99cb9cd17ff26308c2eeb96519dad9a95810e2d1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "73843673"
---
# <a name="host_name-transact-sql"></a>HOST_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Renvoie le nom de la station de travail.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HOST_NAME ()  
```  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Notes  
 Quand le paramètre d'une fonction système est facultatif, la base de données active, l'ordinateur hôte, l'utilisateur du serveur ou l'utilisateur de la base de données sont pris implicitement en considération. Les fonctions intégrées doivent toujours être suivies de parenthèses.  
  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans une clause WHERE, et partout où une expression est autorisée.  
  
> [!IMPORTANT]  
>  L'application cliente fournit le nom de la station de travail et peut fournir des données incorrectes. Ne vous fiez pas à HOST_NAME pour garantir la sécurité.  
  
## <a name="examples"></a>Exemples  
 Cet exemple illustre la création d'une table qui utilise `HOST_NAME()` dans une définition `DEFAULT` pour enregistrer le nom de station de travail des ordinateurs qui insèrent des lignes dans une table dans laquelle les commandes sont consignées.  
  
```  
CREATE TABLE Orders  
   (OrderID     int        PRIMARY KEY,  
    CustomerID  nchar(5)   REFERENCES Customers(CustomerID),  
    Workstation nchar(30)  NOT NULL DEFAULT HOST_NAME(),  
    OrderDate   datetime   NOT NULL,  
    ShipDate    datetime   NULL,  
    ShipperID   int        NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
