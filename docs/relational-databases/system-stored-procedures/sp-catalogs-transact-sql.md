---
title: sp_catalogs (Transact-SQL) | Microsoft Docs
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
- sp_catalogs_TSQL
- sp_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_catalogs
ms.assetid: ebb29ee2-be65-4e09-9c53-e3c6d12633e1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4a5f266872a8e16932fb2fd52c06636ecdcb54e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43030106"
---
# <a name="spcatalogs-transact-sql"></a>sp_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie la liste des catalogues du serveur lié spécifié. Ceci est équivalent aux bases de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_catalogs [ @server_name = ] 'linked_svr'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@server_name =**] **'***linked_svr***'**  
 Nom d'un serveur lié. *linked_svr* est **sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Catalog_name**|**nvarchar(** 128 **)**|Nom du catalogue|  
|**Description**|**nvarchar (** 4000 **)**|Description du catalogue.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie des informations sur les catalogues du serveur lié `OLE DB ODBC Linked Server #3`.  
  
> [!NOTE]  
>  Pour **sp_catalogs** pour fournir des informations utiles, la `OLE DB ODBC Linked Server #3` doit déjà exister.  
  
```  
USE master;  
GO  
EXEC sp_catalogs 'OLE DB ODBC Linked Server #3';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
