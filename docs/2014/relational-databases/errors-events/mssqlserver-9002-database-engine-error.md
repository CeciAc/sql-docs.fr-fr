---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 797e7f0df2d63f4e91746c9a91b18bb1d97af01d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041118"
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9002|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_IS_FULL|  
|Texte du message|Le journal des transactions de la base de données '%.*ls' est plein. Pour savoir pourquoi il est impossible de réutiliser de l'espace dans le journal, consultez la colonne log_reuse_wait_desc dans sys.databases.|  
  
## <a name="explanation"></a>Explication  
 Le journal de la base de données est saturé. La colonne **log_reuse_wait_desc** dans **sys.databases** explique pourquoi il est impossible de réutiliser l’espace dans le journal.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez **sys.databases** pour comprendre pourquoi le journal est plein, puis corrigez la condition. Pour plus d’informations, consultez « Résolution des problèmes en cas de journal des transactions saturé (erreur 9002) » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes liés à un journal des transactions saturé &#40;erreur SQL Server 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
