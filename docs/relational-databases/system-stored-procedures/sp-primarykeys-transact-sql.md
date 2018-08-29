---
title: sp_primarykeys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 072654778b1f2485d0d425f450209ddabcb994fe
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024087"
---
# <a name="spprimarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les colonnes de clés primaires, une ligne par colonne clé, pour la table distante spécifiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@table_server =** ] **' *** serveur_table '*  
 Nom du serveur lié à partir duquel sont retournées les informations de clé primaire. *serveur_de_la_table* est **sysname**, sans valeur par défaut.  
  
 [  **@table_name =** ] **'***table_name***'**  
 Nom de la table pour laquelle les informations de clé primaire sont demandées. *table_name*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@table_schema =** ] **'***table_schema***'**  
 Schéma de la table. *table_schema* est **sysname**, avec NULL comme valeur par défaut. Dans l'environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ceci correspond au propriétaire de la table.  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 Est le nom du catalogue dans lequel spécifié *table_name* réside. Dans l'environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cet argument correspond au nom de la base de données. *table_catalog* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Catalogue de la table|  
|**TABLE_SCHEM**|**sysname**|Schéma de la table|  
|**TABLE_NAME**|**sysname**|Nom de la table.|  
|**COLUMN_NAME**|**sysname**|Nom de la colonne.|  
|**KEY_SEQ**|**Int**|Numéro de séquence de la colonne dans une clé primaire multicolonne.|  
|**PK_NAME**|**sysname**|Identificateur de clé primaire. Retourne NULL s'il n'est pas applicable à la source de données.|  
  
## <a name="remarks"></a>Notes  
 **sp_primarykeys** est exécuté en interrogeant l’ensemble de lignes PRIMARY_KEYS de le **IDBSchemaRowset** interface du fournisseur OLE DB correspondant à *serveur_de_la_table*. Le *table_name*, *table_schema*, *table_catalog*, et *colonne* paramètres sont passés à cette interface pour limiter les lignes retourné.  
  
 **sp_primarykeys** retourne un résultat vide si le fournisseur OLE DB du serveur lié spécifié ne prend pas en charge l’ensemble de lignes PRIMARY_KEYS de le **IDBSchemaRowset** interface.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des colonnes de clé primaires du serveur `LONDON1` pour la table `HumanResources.JobCandidate` dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Distribué des procédures stockées de requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
