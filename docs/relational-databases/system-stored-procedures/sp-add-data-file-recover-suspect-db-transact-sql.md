---
title: sp_add_data_file_recover_suspect_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_data_file_recover_suspect_db
- sp_add_data_file_recover_suspect_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_data_file_recover_suspect_db
ms.assetid: b25262aa-a228-48b7-8739-6581c760b171
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c95b74b5c1875f2a1f1db40ec42e3f3ada87a63
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942362"
---
# <a name="spadddatafilerecoversuspectdb-transact-sql"></a>sp_add_data_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un fichier de données à un groupe de fichiers lorsque la récupération d'une base de données ne peut se terminer en raison d'un espace insuffisant sur le groupe de fichiers (erreur 1105). Une fois le fichier ajouté, cette procédure stockée désactive le paramètre suspect et achève la récupération de la base de données. Les paramètres sont les mêmes que ceux de ALTER DATABASE *database_name* ADD FILE.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_data_file_recover_suspect_db [ @dbName= ] 'database'   
    , [ @filegroup = ] 'filegroup_name'   
    , [ @name = ] 'logical_file_name'   
    , [ @filename= ] 'os_file_name'   
    , [ @size = ] 'size'   
    , [ @maxsize = ] 'max_size'   
    , [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @dbName = ] 'database_ '` Est le nom de la base de données. *base de données* est **sysname**, sans valeur par défaut.  
  
`[ @filegroup = ] 'filegroup_name_ '` Est le groupe de fichiers à laquelle ajouter le fichier. *FILEGROUP_NAME* est **nvarchar (260)** , avec NULL comme valeur par défaut, ce qui indique le fichier primaire.  
  
`[ @name = ] 'logical_file_name_ '` Est le nom utilisé dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour référencer le fichier. Il doit être unique dans le serveur. *nom_fichier_logique* est **nvarchar (260)** , sans valeur par défaut.  
  
`[ @filename = ] 'os_file_name_ '` Le chemin d’accès et nom de fichier est utilisé par le système d’exploitation pour le fichier. Le fichier doit résider sur une instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)]. *os_file_name* est **nvarchar (260)** , sans valeur par défaut.  
  
`[ @size = ] 'size_ '` Est la taille initiale du fichier. *taille* est **nvarchar (20)** , avec NULL comme valeur par défaut. Indiquez un nombre entier sans aucune décimale. Les indications Mo et Ko peuvent être utilisées pour indiquer qu'il s'agit de mégaoctets ou de kilo-octets. La valeur par défaut est Mo. La valeur minimale est 512 Ko. Si *taille* n’est pas spécifié, la valeur par défaut est 1 Mo.  
  
`[ @maxsize = ] 'max_size_ '` Est la taille maximale que peut atteindre le fichier. *max_size* est **nvarchar (20)** , avec NULL comme valeur par défaut. Indiquez un nombre entier sans aucune décimale. Les indications Mo et Ko peuvent être utilisées pour indiquer qu'il s'agit de mégaoctets ou de kilo-octets. La valeur par défaut est Mo.  
  
 Si *max_size* n’est pas spécifié, le fichier croît jusqu'à ce que le disque est plein. Le journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows avertit l'administrateur lorsqu'un disque est sur le point d'être saturé.  
  
`[ @filegrowth = ] 'growth_increment_ '` Est la quantité d’espace ajoutée au fichier chaque fois nouvel espace est nécessaire. *growth_increment* est **nvarchar (20)** , avec NULL comme valeur par défaut. La valeur 0 indique qu'aucun accroissement n'est autorisé. Indiquez un nombre entier sans aucune décimale. La valeur peut être exprimée en Mo, en Ko ou en pourcentage (%). Lorsque % est spécifié, la taille de l'incrément de croissance est le pourcentage spécifié de la taille du fichier au moment où l'incrémentation a lieu. Si un nombre est mentionné sans spécifier Mo, Ko ou %, la valeur par défaut est Mo.  
  
 Si *growth_increment* a la valeur NULL, la valeur par défaut est 10 %, et la valeur minimale est de 64 Ko. La taille spécifiée est arrondie à la valeur multiple de 64 Ko la plus proche.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="permissions"></a>Autorisations  
 Exécution reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe. Ces autorisations ne sont pas transférables.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la base de données `db1` a été déclarée suspecte au cours de sa récupération en raison d'un espace insuffisant (erreur 1105) dans le groupe de fichiers `fg1`.  
  
```  
USE master;  
GO  
EXEC sp_add_data_file_recover_suspect_db db1, fg1, file2,  
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_file2.mdf', '1MB';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
