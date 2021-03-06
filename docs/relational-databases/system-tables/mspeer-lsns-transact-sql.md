---
title: MSpeer_lsns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
author: stevestein
ms.author: sstein
ms.openlocfilehash: c0d31de11ed7d41ecca409589f3daa25c85f1146
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085774"
---
# <a name="mspeerlsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **Mspeer_lsns** table est utilisée pour mapper chaque transaction à un abonnement dans une topologie de réplication d’égal à égal. Cette table est stockée dans chaque base de données de publication, dans une topologie de réplication d'égal à égal dans la base de données d'abonnement de tous les Abonnés à une publication d'égal à égal. Pour plus d’informations sur ce type de topologie de réplication transactionnelle, consultez [Peer-to-Peer la réplication transactionnelle](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md). Cette table est stockée dans la base de données de publication.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identifie un numéro de séquence d'enregistrement d'égal à égal.|  
|**last_updated**|**datetime**|Le **datetime** à laquelle la dernière mise à jour de la ligne a été effectuée.|  
|**originator**|**sysname**|Nom du serveur de publication à l'origine de la transaction|  
|**originator_db**|**sysname**|Nom de la base de données d'où provient la transaction|  
|**originator_publication**|**sysname**|Nom de la publication d'où provient la transaction|  
|**originator_publication_id**|**Int**|Identificateur de la publication d'où provient la transaction|  
|**originator_db_version**|**Int**|Identifie le numéro de version de la base de données d'origine.|  
|**originator_lsn**|**int**|Identifie le numéro de séquence d'enregistrement dans la publication d'origine.|  
|**originator_version**|**int**|Spécifie le numéro de version du serveur de publication.|  
|**originator_id**|**smallint**|Identifie chaque nœud dans la topologie pour les besoins de la détection de conflit. Pour plus d’informations, voir [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
