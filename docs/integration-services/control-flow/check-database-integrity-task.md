---
title: Vérifier l’intégrité de la base de données, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 676bbf9fb96521ceaa24f58b448182506307f691
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298398"
---
# <a name="check-database-integrity-task"></a>Tâche Vérifier l'intégrité de la base de données

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La tâche Vérifier l'intégrité de la base de données contrôle l'allocation et l'intégrité de la structure de tous les objets de la base de données spécifiée. La tâche peut vérifier une ou plusieurs bases de données et vous pouvez indiquer si vous souhaitez également contrôler les index de base de données.  
  
 La tâche Vérifier l'intégrité de la base de données encapsule l'instruction DBCC CHECKDB. Pour plus d’informations, consultez [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).  
  
## <a name="configuration-of-the-check-database-integrity-task"></a>Configuration de la tâche Vérifier l'intégrité de la base de données  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Vérifier l’intégrité de la base de données &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
