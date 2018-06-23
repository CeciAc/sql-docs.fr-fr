---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: dc95a21fa1c3bc980e798a7f36ea4a6b19efdce8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038130"
---
# <a name="mssqleng003724"></a>MSSQL_ENG003724
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3724|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de %1! le %2! '%3!' parce qu'il est utilisé pour la réplication.|  
  
## <a name="explanation"></a>Explication  
 Lorsque des objets d'une base de données sont répliqués, ils sont marqués comme étant répliqués dans la table système **sysarticles** (publications transactionnelles ou d'instantanés) ou dans la table système **sysmergearticles** (publications de fusion). Si vous tentez de supprimer un objet répliqué, cette erreur est générée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que l'objet de base de données n'est pas répliqué avant d'essayer de le supprimer. Exemple :  
  
-   Si l'erreur se produit dans la base de données de publication, supprimez l'article de la publication avant de supprimer l'objet. Pour plus d’informations, consultez [Ajouter et supprimer des articles de publications existantes](publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Si l'erreur se produit dans la base de données d'abonnement, supprimez l'abonnement avant de supprimer l'objet. Pour plus d’informations, consultez [S’abonner à des publications](subscribe-to-publications.md). Dans le cas d'abonnements aux publications transactionnelles, il est possible de supprimer l'abonnement à un article individuel plutôt qu'à la publication complète. Pour plus d’informations, consultez [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).  
  
 Si cette erreur se produit dans une base de données qui n’est pas répliquée, exécutez [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) pour vérifier que les objets de la base de données ne sont pas marqués comme étant répliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
