---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 526c5b0bb1b7c5dd0d7cf1485f7e399b6f1fbff9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666974"
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|4929|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de modifier le % S_MSG ' %. * ls', car elle est publiée pour la réplication.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit généralement lorsque vous tentez de supprimer la contrainte de clé primaire d'une table publiée pour la réplication transactionnelle. Comme la réplication transactionnelle nécessite une clé primaire pour chaque table publiée, la contrainte ne peut pas être supprimée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour supprimer la contrainte, commencez par supprimer l'article associé à la table. Pour plus d’informations, consultez [Ajouter et supprimer des articles de publications existantes](publish/add-articles-to-and-drop-articles-from-existing-publications.md). Si cette erreur se produit dans une base de données qui n’est pas répliquée, exécutez [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) pour vérifier que les objets de la base de données ne sont pas marqués comme étant répliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
