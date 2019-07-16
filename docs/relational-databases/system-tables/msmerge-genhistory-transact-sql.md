---
title: MSmerge_genhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf9c38fe71c1282b19b947fc1771714dd138c45a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017701"
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_genhistory** table contient une ligne pour chaque génération connue de l’abonné (au sein de la période de rétention). Elle permet d'éviter l'envoi de générations communes au cours des échanges et de resynchroniser les Abonnés restaurés à partir de sauvegardes. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|Identificateur global des modifications identifiées par la génération au niveau de l'Abonné.|  
|**pubid**|**uniqueidentifier**|L’identificateur de la publication.|  
|**génération**|**bigint**|Valeur de génération.|  
|**art_nick**|**Int**|Le surnom pour l’article.|  
|**Surnoms**|**varbinary(1001)**|Liste des surnoms des autres Abonnés qui possèdent déjà cette génération. L'utilisation de cet argument permet d'éviter l'envoi d'une génération à un Abonné qui a déjà consulté ces modifications. Les surnoms de cette liste sont classés par ordre alphabétique afin d'augmenter l'efficacité des recherches. Si le nombre de surnoms dépasse les capacités de ce champ, ces derniers ne bénéficieront pas de l'optimisation.|  
|**colDate**|**datetime**|Date d'ajout de la génération actuelle à la table.|  
|**genstatus**|**tinyint**|Le statut de la génération est le suivant :<br /><br /> **0** = ouvert.<br /><br /> **1** = fermé.<br /><br /> **2** = fermé et issu d’un autre abonné.|  
|**changecount**|**int**|Nombre de modifications réfléchies dans une génération donnée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
