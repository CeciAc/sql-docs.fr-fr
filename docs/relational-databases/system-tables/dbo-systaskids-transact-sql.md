---
title: dbo.systaskids (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- systaskids_TSQL
- dbo.systaskids
- systaskids
- dbo.systaskids_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systaskids system table
ms.assetid: 45c56d89-4160-4d84-80bf-a7a05488792d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a40bd9acc3961a77cb69bc24fc37f5e89192c34a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802263"
---
# <a name="dbosystaskids-transact-sql"></a>dbo.systaskids (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient un mappage des tâches créées dans des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers des travaux [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans la version actuelle. Cette table est stockée dans le **msdb** base de données.  
  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id_tâche**|**Int**|ID de la tâche|  
|**job_id**|**uniqueidentifier**|ID du travail auquel la tâche est mappée.|  
  
  
