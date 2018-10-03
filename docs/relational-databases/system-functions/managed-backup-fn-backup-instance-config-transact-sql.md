---
title: managed_backup.fn_backup_instance_config (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_backup_instance_config
- smart_admin.fn_backup_instance_config_TSQL
- fn_backup_instance_config_TSQL
- smart_admin.fn_backup_instance_config
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_instance_config
- fn_backup_instance_config
ms.assetid: 2382a547-c0c9-4e1d-87c9-d8526192eb5a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2be102c3d1b967d4376385b2bc20f61e16ecbde7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627540"
---
# <a name="managedbackupfnbackupinstanceconfig-transact-sql"></a>managed_backup.fn_backup_instance_config (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne avec les paramètres de configuration par défaut de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour l'instance de SQL Server.  
  
 Utilisez cette procédure stockée pour consulter ou déterminer les paramètres de configuration par défaut de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] actifs pour l'instance de SQL Server.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
managed_backup.fn_backup_db_config ()  
```  
  
##  <a name="Arguments"></a> Arguments  
 None  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|is_smart_backup_enabled|INT|Affiche 1 lorsque la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est activée et 0 lorsque la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est désactivée.|  
|credential_name|SYSNAME|Informations d'identification SQL par défaut utilisées pour authentifier le stockage.|  
|retention_days|INT|Période de rétention par défaut définie au niveau de l'instance.|  
|storage_url|NVARCHAR (1024)|URL du compte de stockage par défaut définie au niveau de l'instance.|  
|encryption_algorithm|SYSNAME|Nom de l’algorithme de chiffrement. A la valeur NULL, si le chiffrement n'est pas spécifié.|  
|encryptor_type|NVARCHAR (32)|Type de chiffreur utilisé : certificat ou clé asymétrique A la valeur NULL, si aucun chiffreur n'est spécifié.|  
|encryptor_name|SYSNAME|Nom du certificat ou de la clé asymétrique. A la valeur NULL, si aucun nom n'est spécifié.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **db_backupoperator** rôle de base de données avec **ALTER ANY CREDENTIAL** autorisations. L’utilisateur ne doit pas être refusé **VIEW ANY DEFINITION** autorisations.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie la configuration par défaut de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour l'instance sur laquelle elle est exécutée :  
  
```  
Use msdb;  
GO  
SELECT * FROM managed_backup.fn_backup_instance_config ();  
  
```  
  
  
