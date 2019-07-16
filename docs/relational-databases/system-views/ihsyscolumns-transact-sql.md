---
title: IHsyscolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: a432685809676f997049940ea5aa1ce43dc38a60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029630"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **IHsyscolumns** vue expose des informations sur les colonnes pour les articles publiés à partir d’un serveur non-SQL. Cette vue est stockée dans la propriété distributiondatabase.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de la colonne ou du paramètre de la procédure.|  
|**id**|**int**|Identificateur d'objet de la table à laquelle cette colonne appartient ou identificateur de la procédure stockée à laquelle ce paramètre est associé.|  
|**xtype**|**tinyint**|Le type de stockage physique provenant [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|Identificateur du type de données étendu défini par l'utilisateur.|  
|**length**|**bigint**|La longueur maximale de stockage physique à partir [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**XScale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**int**|Identificateur de colonne ou de paramètre.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Identificateur de la valeur par défaut pour cette colonne.|  
|**Domaine**|**int**|Identificateur de la règle ou de la contrainte CHECK pour cette colonne.|  
|**nombre**|**int**|Le numéro de sous-procédure pour les procédures groupées (**0** pour les entrées).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Déplacement dans la ligne où cette colonne apparaît.|  
|**collationid**|**Int**|Identificateur du classement de la colonne. NULL pour les colonnes non basées sur les caractères.|  
|**language**|**Int**|Identificateur du langage de la colonne.|  
|**status**|**Int**|La bitmap utilisée pour décrire une propriété de la colonne ou du paramètre :<br /><br /> **0 x 08** = colonne autorise les valeurs null.<br /><br /> **0 x 10** = remplissage ANSI étaient actifs lorsque **varchar** ou **varbinary** colonnes ont été ajoutées. Les espaces à droite sont conservés pour **varchar** et les zéros de fin sont conservés pour **varbinary** colonnes.<br /><br /> **0 x 40** = paramètre est un paramètre de sortie.<br /><br /> **0 x 80** = colonne est une colonne d’identité.|  
|**type**|**Int**|Le type de stockage physique provenant [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**usertype**|**tinyint**|L’ID de type de données défini par l’utilisateur à partir de [sys.systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**PREC**|**Int**|Niveau de précision de cette colonne.|  
|**scale**|**int**|Échelle de cette colonne.|  
|**IsComputed**|**Int**|L’indicateur qui spécifie si la colonne est calculée :<br /><br /> **0** = non calculée.<br /><br /> **1** = calculée.|  
|**isoutparam**|**int**|Indique si le paramètre de la procédure est un paramètre de sortie ou non :<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Indique si les colonnes autorisent les valeurs NULL :<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**classement**|**Int**|Le nom du classement de la colonne. NULL pour les colonnes non basées sur les caractères.|  
|**tdscollation**|**int**|Nom du classement de la colonne lors du retour dans un flux de données tabulaires (TDS).|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
