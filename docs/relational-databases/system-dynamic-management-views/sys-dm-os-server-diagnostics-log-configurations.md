---
title: Sys.dm_os_server_diagnostics_log_configurations | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e5a57c9617191a53545e590aa6695d82c0ee6d30
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Retourne une ligne avec la configuration actuelle pour le journal de diagnostics du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces paramètres de propriété déterminent si la journalisation des diagnostics est activée ou désactivée, et indiquent l'emplacement, le nombre et la taille des fichiers journaux.  
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|Indique si la journalisation est activée ou désactivée.<br /><br /> 1 = La journalisation des diagnostics est activée<br /><br /> 0 = La journalisation des diagnostics est désactivée|  
|max_size|**int**|Taille maximale, en mégaoctets, que peut atteindre chacun des journaux de diagnostics. La valeur par défaut est 100 MB.|  
|max_files|**int**|Nombre maximal de fichiers journaux de diagnostics qui peuvent être stockés sur l'ordinateur avant qu'ils ne soient recyclés pour créer de nouveaux journaux de diagnostics.|  
|path|**nvarchar (260)**|Chemin d'accès qui indique l'emplacement des journaux de diagnostics. L’emplacement par défaut est \<\MSSQL\Log > dans le dossier d’installation de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de cluster de basculement.|  
  
## <a name="permissions"></a>Permissions  
 Requiert les autorisations VIEW SERVER STATE sur l'instance de cluster de basculement SQL Server.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise sys.dm_os_server_diagnostics_log_configurations pour retourner les paramètres de propriété pour les journaux de diagnostics du basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program Files\Microsoft SQL Server\MSSQL13\MSSQL\Log >|10|10|  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et lire le journal de diagnostic de l’instance de cluster de basculement](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  