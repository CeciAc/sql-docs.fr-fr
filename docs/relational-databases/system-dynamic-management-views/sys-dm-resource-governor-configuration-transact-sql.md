---
title: Sys.dm_resource_governor_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_resource_governor_configuration_TSQL
- dm_resource_governor_configuration
- sys.dm_resource_governor_configuration
- sys.dm_resource_governor_configuration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_configuration dynamic management view
ms.assetid: c89aab6a-0434-4ce6-af8c-f8a1a3284e38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b36a4c07d37ba55a9cd4e4573d144f19259f2cfe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832417"
---
# <a name="sysdmresourcegovernorconfiguration-transact-sql"></a>sys.dm_resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne qui contient l'état de configuration en mémoire actuel du gouverneur de ressources.  
  

|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**Int**|ID de la fonction classifieur utilisée actuellement par le gouverneur de ressources. Retourne la valeur 0 si aucune fonction n'est utilisée. N'accepte pas la valeur NULL.<br /><br /> **Remarque :** cette fonction est utilisée pour classer les nouvelles demandes et utilise des règles pour router ces demandes vers le groupe de charges de travail approprié. Pour plus d’informations, consultez [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).|  
|is_reconfiguration_pending|**bit**|Indique si des modifications ont été apportées ou non à un groupe ou un pool à l'aide de l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE mais qu'elles n'ont pas été appliquées à la configuration en mémoire. L'une des valeurs suivantes est retournée :<br /><br /> 0 - Une instruction de reconfiguration n'est pas requise.<br /><br /> 1 - Une instruction de reconfiguration ou un redémarrage du serveur est requis pour que les modifications de configuration en attente soient appliquées.<br /><br /> **Remarque :** la valeur retournée est toujours 0 lorsque le gouverneur de ressources est désactivé.<br /><br /> N'accepte pas la valeur NULL.|  
|max_outstanding_io_per_volume|**Int**|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre maximal d'E/S en attente par volume.|  
  
## <a name="remarks"></a>Notes  
 Cette vue de gestion dynamique montre la configuration en mémoire. Pour consulter les métadonnées de configuration stockées, utilisez l'affichage catalogue correspondant.  
  
 L'exemple suivant indique comment obtenir et comparer les valeurs de métadonnées stockées et les valeurs en mémoire de la configuration du gouverneur de ressources.  
  
```  
USE master;  
go  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
go  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
go  
```  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Sys.resource_governor_configuration &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-configuration-transact-sql.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  

