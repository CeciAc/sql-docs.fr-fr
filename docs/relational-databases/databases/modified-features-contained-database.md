---
title: Fonctionnalités modifiées (base de données autonome) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c85d6e423c63337be4d2eaf2f96c420a4f6ad33
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68067340"
---
# <a name="modified-features-contained-database"></a>Fonctionnalités modifiées (base de données autonome)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les fonctionnalités suivantes ont été modifiées pour être prises en charge par une base de données partiellement autonome. Les fonctionnalités sont généralement modifiées de façon à ce qu'elles ne traversent pas la limite de base de données.  
  
 Pour plus d’informations, consultez [Bases de données autonomes](../../relational-databases/databases/contained-databases.md).  
  
## <a name="alter-database"></a>ALTER DATABASE  
  
### <a name="application-level"></a>Niveau de l'application  
 Lors de l'utilisation de l'instruction ALTER DATABASE à partir d'une base de données autonome, la syntaxe est différente de celle utilisée pour une base de données non autonome. Cette différence inclut des restrictions sur les éléments de l'instruction qui s'étendent au-delà de la base de données, au niveau de l'instance. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
### <a name="instance-level"></a>Niveau de l'instance  
 La syntaxe de l'instruction ALTER DATABASE en cas d'utilisation hors d'une base de données autonome diffère de celle utilisée pour les bases de données non autonomes. Ces modifications empêchent de dépasser la limite de base de données. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="create-database"></a>CREATE DATABASE  
 La syntaxe CREATE DATABASE pour une base de données autonome diffère de celle pour une base de données non autonome. Consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) pour plus d’informations sur les nouvelles exigences et autorisations relatives à la syntaxe.  
  
## <a name="temporary-tables"></a>Tables temporaires  
 Les tables temporaires locales sont autorisées dans une base de données autonome, mais leur comportement est différent dans les bases de données non autonomes. Dans les bases de données sans relation contenant-contenu, les données de table temporaire sont classées selon le classement de **tempdb**. Dans une base de données autonome, les données de la table temporaire sont classées selon le classement de cette base de données.  
  
 Toutes les métadonnées associées aux tables temporaires (par exemple, les noms de table et de colonne, les index, etc.) figurent dans le classement de catalogue.  
  
 Les contraintes nommées ne peuvent pas être utilisées dans les tables temporaires.  
  
 Les tables temporaires ne peuvent pas faire référence aux types définis par l'utilisateur, aux collections de schémas XML ou aux fonctions définies par l'utilisateur.  
  
## <a name="collation"></a>Classement  
 Dans le modèle de base de données non autonome, il existe trois types de classement distincts : classement de base de données, classement d’instance et classement tempdb. Les bases de données autonomes utilisent uniquement deux classements, le classement de base de données et le nouveau classement de catalogue. Consultez [Classements de base de données autonome](../../relational-databases/databases/contained-database-collations.md) pour plus d’informations sur le classement de bases de données autonomes.  
  
## <a name="user-options"></a>Options utilisateur  
 Au moment d’activer les bases de données autonomes, l’option [user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) doit avoir la valeur 0 pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Classements de base de données autonome](../../relational-databases/databases/contained-database-collations.md)   
 [Bases de données autonomes](../../relational-databases/databases/contained-databases.md)  
  
  
