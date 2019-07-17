---
title: Sys.column_store_dictionaries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f675e4d0d40bf9e1db4bf2de6b66b1acfc039873
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140019"
---
# <a name="syscolumnstoredictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque dictionnaire utilisé dans des index columnstore optimisés en mémoire xVelocity. Les dictionnaires sont utilisés pour encoder certains, mais pas tous les types de données, par conséquent, certaines colonnes d'un index columnstore n'ont pas de dictionnaires. Un dictionnaire peut exister en tant que dictionnaire principal (pour tous les segments) et éventuellement pour d'autres dictionnaires secondaires utilisés pour un sous-ensemble des segments de la colonne.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|ID du segment ou de l'index d'arbre B (B-tree) pour la table ayant cet index columnstore.|  
|**column_id**|**int**|ID de la colonne columnstore en commençant par 1. La première colonne a ID = 1, la deuxième colonne a ID = 2, etc.|  
|**dictionary_id**|**Int**|Il peut y avoir deux types de dictionnaires : globales et locales, associés à un segment de colonne. Un dictionary_id 0 représente le dictionnaire global qui est partagé entre tous les segments de colonne (une pour chaque groupe de lignes) pour cette colonne.|  
|**version**|**int**|Version du format de dictionnaire.|  
|**type**|**Int**|Type de dictionnaire :<br /><br /> 1 - dictionnaire de hachage contenant **int** valeurs<br /><br /> 2 - non utilisé<br /><br /> 3 - dictionnaire de hachage contenant des valeurs de chaîne<br /><br /> 4 - dictionnaire de hachage contenant **float** valeurs<br /><br /> Pour plus d’informations sur les dictionnaires, consultez [Guide des index Columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**Int**|Le dernier ID de données dans le dictionnaire.|  
|**entry_count**|**bigint**|Nombre d'entrées dans le dictionnaire.|  
|**on_disc_size**|**bigint**|Taille du dictionnaire en octets.|  
|**partition_id**|**bigint**|Indique l'ID de partition. Unique dans une base de données.|  
  
## <a name="permissions"></a>Autorisations  
 Toutes les colonnes requièrent au moins l'autorisation VIEW DEFINITION sur la table. Les colonnes suivantes retournent null à moins que l’utilisateur ait également **sélectionnez** autorisation : last_id, entry_count, data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guide des index columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Guide des index columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

