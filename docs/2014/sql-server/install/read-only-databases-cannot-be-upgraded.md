---
title: Bases de données en lecture seule ne peut pas être mis à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 414b26cf860ab32bb11beaa1ccbef3316c68f557
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093368"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Les bases de données en lecture seule ne peuvent pas être mises à niveau
  Le Conseiller de mise à niveau a déterminé que certaines bases de données sur cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas être mises à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Une base de données en lecture seule a été détectée. Le programme d'installation doit pouvoir écrire dans la base de données pour la mettre à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque personne n’utilise la base de données, utilisez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ou l’instruction ALTER DATABASE pour modifier la base de données en lecture-écriture. L'instruction suivante affecte à la base de données l'attribut lecture-écriture.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Pour plus d'informations sur l'instruction ALTER DATABASE, consultez la rubrique « ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)]) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
