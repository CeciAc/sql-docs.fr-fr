---
title: IHcolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHcolumns_TSQL
- IHcolumns
dev_langs:
- TSQL
helpviewer_keywords:
- IHcolumns system table
ms.assetid: 5bb027e5-5279-487b-9c33-5f402987253c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c5d05f2667b6f7196338b182f2b9cca1a84e7b6e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802441"
---
# <a name="ihcolumns-transact-sql"></a>IHcolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **IHcolumns** (table système) contient une ligne pour chaque colonne publiée. Cette table est utilisée pour définir comment les types de données de colonne à partir de la non de publication non-SQL Server seront représentées lors de la publié, qui mappe les types de données entre un systèmes de gestion de base de données (SGBD) non SQL Server et SQL Server. Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**Int**|Identifie une colonne publiée.|  
|**publishercolumn_id**|**Int**|Associe une colonne publiée avec les métadonnées de colonne stockées dans le [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) (table système).|  
|**nom**|**sysname**|Spécifie le nom de la colonne.|  
|**article_id**|**Int**|Identifie l'article auquel appartient la colonne.|  
|**column_ordinal**|**Int**|Identifie la colonne par ordre.|  
|**mapped_type**|**tinyint**|Type de données colonne de la colonne de destination chez l'abonné.|  
|**mapped_length**|**bigint**|Longueur de la colonne chez l'abonné.|  
|**mapped_prec**|**Int**|Précision de la colonne chez l'abonné.|  
|**mapped_scale**|**Int**|Échelle de la colonne chez l'abonné.|  
|**mapped_nullable**|**bit**|Indique si la colonne sur l’abonné accepte les valeurs NULL, où **1** signifie que les valeurs NULL sont acceptées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;vue système&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
