---
title: Sys.server_triggers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: caed89727f8fe6670db1b2531c0c2641ed92b38b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024588"
---
# <a name="sysservertriggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient l'ensemble de tous les déclencheurs DDL de niveau serveur avec un type object_type de valeur TR ou TA. Dans le cas des déclencheurs CLR, l’assembly doit être chargé dans le **master** base de données. Tous les noms de déclencheurs DDL au niveau du serveur existent dans une étendue unique et globale.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du déclencheur.|  
|**object_id**|**Int**|ID de l'objet.|  
|**parent_class**|**tinyint**|Classe du parent. Est toujours :<br /><br /> 100 = serveur|  
|**parent_class_desc**|**nvarchar(60)**|Description d'une classe de parent. Est toujours :<br /><br /> SERVER.|  
|**parent_id**|**Int**|Toujours 0 pour les déclencheurs sur SERVER.|  
|**type**|**char(2)**|Type d’objet :<br /><br /> TA = Déclencheur assembly (CLR)<br /><br /> TR = Déclencheur SQL|  
|**type_desc**|**nvarchar(60)**|Description de la classe du type d'objet.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|Date de création du déclencheur.|  
|**modify_date**|**datetime**|Date de la dernière modification du déclencheur à l'aide de l'instruction ALTER.|  
|**is_ms_shipped**|**bit**|Déclencheur créé pour l'utilisateur par un composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interne.|  
|**is_disabled**|**bit**|1 = Déclencheur désactivé.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
