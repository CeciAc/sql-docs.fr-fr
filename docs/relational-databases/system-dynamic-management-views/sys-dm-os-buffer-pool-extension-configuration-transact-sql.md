---
title: Sys.dm_os_buffer_pool_extension_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_buffer_pool_extension_configuration
- sys.dm_os_buffer_pool_extension_configuration_TSQL
- dm_os_buffer_pool_extension_configuration_TSQL
- sys.dm_os_buffer_pool_extension_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_pool_extension_configuration dynamic management view
ms.assetid: d52cc481-4d29-4f33-b63d-231ec35d092f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef0eea139b491c565b8635daf69cefff61492688
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755837"
---
# <a name="sysdmosbufferpoolextensionconfiguration-transact-sql"></a>sys.dm_os_buffer_pool_extension_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Retourne les informations de configuration de l'extension du pool de mémoires tampons dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Retourne une ligne pour chaque fichier d'extension du pool de mémoires tampons.  
  

  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|path|**nvarchar**(256)|Chemin d'accès et nom de fichier du cache d'extension du pool de mémoires tampons. Autorise la valeur Null.|  
|file_id|**Int**|ID du fichier d'extension du pool de mémoires tampons. N'accepte pas la valeur NULL.|  
|state|**Int**|État de la fonctionnalité d'extension du pool de mémoires tampons. N'accepte pas la valeur NULL.<br /><br /> 0 : Extension du pool de mémoires tampons désactivée<br /><br /> 1 : Désactivation de l'extension du pool de mémoires tampons<br /><br /> 2 : réservé pour un usage ultérieur<br /><br /> 3 : Activation de l'extension du pool de mémoires tampons<br /><br /> 4 : Réservé pour un usage ultérieur<br /><br /> 5 : Extension du pool de mémoires tampons activée|  
|state_description|**nvarchar**(60)|Décrit l'état de la fonctionnalité d'extension du pool de mémoires tampons. Autorise la valeur NULL.<br /><br /> 0 = BUFFER POOL EXTENSION DISABLED<br /><br /> 1 = BUFFER POOL EXTENSION ENABLED|  
|current_size_in_kb|**bigint**|Taille actuelle du fichier d'extension du pool de mémoires tampons. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-configuration-buffer-pool-extension-information"></a>A. Retourner les informations de configuration de l'extension du pool de mémoires tampons  
 L'exemple suivant retourne toutes les colonnes de la vue de gestion dynamique sys.dm_os_buffer_pool_extension_configruation.  
  
```sql  
SELECT path, file_id, state, state_description, current_size_in_kb  
FROM sys.dm_os_buffer_pool_extension_configuration;  
```  
  
### <a name="b-returning-the-number-of-cached-pages-in-the-buffer-pool-extension-file"></a>B. Retourner le nombre de pages mises en cache dans le fichier d'extension du pool de mémoires tampons  
 L'exemple suivant retourne le nombre de pages mises en cache dans chaque fichier d'extension de pool de mémoires tampons.  
  
```sql  
SELECT COUNT(*) AS cached_pages_count  
FROM sys.dm_os_buffer_descriptors  
WHERE is_in_bpool_extension <> 0  
;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du Pool de mémoires tampons](../../database-engine/configure-windows/buffer-pool-extension.md)   
 [sys.dm_os_buffer_descriptors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-descriptors-transact-sql.md)  
  
  
