---
title: Sys.syscolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscolumns
- sys.syscolumns_TSQL
- syscolumns_TSQL
- syscolumns
dev_langs:
- TSQL
helpviewer_keywords:
- syscolumns system table
- sys.syscolumns compatibility view
ms.assetid: 863fd87b-ff33-4ac5-9aa9-df21140681da
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c158533188db7e3d72235a69bff1b14546a1a1a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089239"
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Retourne une ligne pour chaque colonne des tables et des vues, et une ligne pour chaque paramètre des procédures stockées de la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de la colonne ou du paramètre de la procédure|  
|**id**|**Int**|Identificateur d'objet de la table à laquelle cette colonne appartient, ou ID de la procédure stockée à laquelle ce paramètre est associé|  
|**xtype**|**tinyint**|Type de stockage physique provenant **sys.types**.|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Identificateur de type de données étendu défini par l'utilisateur Déborde ou retourne la valeur NULL si le nombre de types de données dépasse 32 767.|  
|**length**|**smallint**|Longueur maximale de stockage physique provenant **sys**. **types**.|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**XScale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**smallint**|Identificateur de colonne ou de paramètre|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Identificateur de la valeur par défaut pour cette colonne|  
|**Domaine**|**Int**|Identificateur de la règle ou de la contrainte CHECK pour cette colonne|  
|**nombre**|**smallint**|Numéro de sous-procédure pour les procédures groupées.<br /><br /> 0 = entrées qui ne décrivent pas une procédure|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary(8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**smallint**|Décalage dans la ligne où apparaît cette colonne.|  
|**collationid**|**int**|ID du classement de la colonne. NULL pour les colonnes de type non caractère.|  
|**status**|**tinyint**|Bitmap servant à décrire une propriété de la colonne ou du paramètre :<br /><br /> 0x08 = La colonne autorise les valeurs NULL.<br /><br /> 0 x 10 = remplissage ANSI étaient actifs lorsque **varchar** ou **varbinary** colonnes ont été ajoutées. Les espaces à droite sont conservés pour **varchar** et les zéros de fin sont conservés pour **varbinary** colonnes.<br /><br /> 0x40 = Le paramètre est un paramètre de sortie (OUTPUT).<br /><br /> 0x80 = La colonne est une colonne d'identité.|  
|**type**|**tinyint**|Type de stockage physique provenant **sys**. **types**.|  
|**usertype**|**smallint**|ID de type de données défini par l’utilisateur à partir de **sys.types**. Déborde ou retourne la valeur NULL si le nombre de types de données dépasse 32 767.|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**PREC**|**smallint**|Niveau de précision de cette colonne<br /><br /> -1 = **xml** ou type de valeur élevée.|  
|**scale**|**int**|Échelle de cette colonne<br /><br /> NULL = le type de données est non numérique.|  
|**IsComputed**|**int**|Indicateur signalant si la colonne est calculée :<br /><br /> 0 = Non calculée<br /><br /> 1 = Calculée|  
|**isoutparam**|**int**|Indique si le paramètre de la procédure est un paramètre de sortie ou non :<br /><br /> 1 = True<br /><br /> 0 = False|  
|**IsNullable**|**int**|Indique si les colonnes autorisent les valeurs NULL :<br /><br /> 1 = True<br /><br /> 0 = False|  
|**classement**|**sysname**|Nom du classement de la colonne. NULL s'il ne s'agit pas d'une colonne de type caractère.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
