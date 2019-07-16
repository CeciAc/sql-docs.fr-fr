---
title: Core.sp_update_data_source (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_data_source
- sp_update_data_source_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_data_source
- management data warehouse, data collector stored procedures
- core.sp_update_data_source stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 66b95f96-6df7-4657-9b3c-86a58c788ca5
author: stevestein
ms.author: sstein
ms.openlocfilehash: a840c749222cc7c01fa1b1ff5a27489e0e9d322a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942468"
---
# <a name="corespupdatedatasource-transact-sql"></a>core.sp_update_data_source (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met à jour une ligne existante ou insère une nouvelle ligne dans la table core.source_info_internal de l'entrepôt de données de gestion. Cette procédure est appelée par le composant runtime du collecteur de données chaque fois qu'un package de téléchargement commence à télécharger des données dans l'entrepôt de données de gestion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
core.sp_update_data_source [ @collection_set_uid = ] 'collection_set_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @days_until_expiration = ] days_until_expiration  
    , [ @source_id = ] source_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [ @collection_set_uid =] '*collection_set_uid*'  
 GUID du jeu d'éléments de collecte. *collection_set_uid* est **uniqueidentifier**, sans valeur par défaut. Pour obtenir le GUID, interrogez la vue dbo.syscollector_collection_sets dans la base de données msdb.  
  
 [ @machine_name =] '*Nom_Ordinateur*'  
 Nom du serveur sur lequel réside le jeu d'éléments de collecte. *Nom_Ordinateur* est **sysname** sans valeur par défaut.  
  
 [ @named_instance =] '*instance_nommée*'  
 Nom de l'instance pour le jeu d'éléments de collecte. *instance_nommée* est **sysname**, sans valeur par défaut.  
  
> [!NOTE]  
>  *instance_nommée* doit être le nom d’instance complet, qui se compose du nom de l’ordinateur et le nom d’instance sous la forme *computername*\\*instancename*.  
  
 [ @days_until_expiration =] *days_until_expiration*  
 Nombre de jours restants dans la période de rétention des données d'instantanés. *days_until_expiration* est **smallint**.  
  
 [ @source_id =] *source_id*  
 Identificateur unique de la source de la mise à jour. *Source_ID* est **int** et est retourné en tant que sortie.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu'un package de téléchargement commence à télécharger des données dans l'entrepôt de données de gestion, le composant runtime du collecteur de données appelle core.sp_update_data_source. La table core.source_info_internal est mise à jour si l'une des modifications suivantes a été apportée depuis le dernier téléchargement :  
  
-   Un nouveau jeu d'éléments de collecte a été ajouté.  
  
-   La valeur de days_until_expiration a changé.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **mdw_writer** (avec autorisation EXECUTE) rôle fixe de base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant met à jour la source de données (dans le cas présent, le jeu d'éléments de collecte Utilisation du disque), définit le nombre de jours avant l'expiration et retourne l'identificateur de la source. Dans l'exemple, l'instance par défaut est utilisée.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @source_id int;  
EXEC core.sp_update_data_source   
@collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
@machine_name = '<computername>',  
@named_instance = 'MSSQLSERVER',  
@days_until_expiration = 10,  
@source_id = @source_id OUTPUT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Entrepôt de données de gestion](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
