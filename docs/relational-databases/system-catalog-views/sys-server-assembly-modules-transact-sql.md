---
title: Sys.server_assembly_modules (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eeb90ab264d2ba8fd9ca2213faca6fd4a872e3d9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient pour chaque module d'assembly une ligne destinée aux déclencheurs de niveau serveur de type TA. Cette vue mappe des déclencheurs d'assembly à leur implémentation CLR sous-jacente. Vous pouvez joindre cette relation à **sys.server_triggers**. L’assembly doit être chargé dans le **master** base de données. C'est le tuple (object_id) qui correspond à la clé de cette relation.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Contre référence de FOREIGN KEY à l'objet sur lequel ce module d'assembly est défini.|  
|**assembly_id**|**int**|ID de l'assembly à partir duquel ce module a été créé. L'assembly doit être chargé dans la base de données master.|  
|**assembly_class**|**sysname**|Nom de la classe dans l'assembly définissant ce module.|  
|**assembly_method**|**sysname**|Nom de la méthode dans la classe définissant ce module. Correspond à la valeur NULL dans le cas de fonctions d'agrégation (AF, aggregate functions).|  
|**execute_as_principal_id**|**int**|ID de l'instruction d'exécution en tant que principal de serveur (EXECUTE AS).<br /><br /> Valeur NULL par défaut ou dans le cas de l'instruction EXECUTE AS CALLER.<br /><br /> ID du principal spécifié si EXECUTE AS SELF EXECUTE AS \<principal >.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  