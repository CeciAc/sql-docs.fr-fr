---
title: Configurer les journaux d’erreurs de SQL Server Agent (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 97107d636f03d9cec2b74fe25b65c9d90ad848a0
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267441"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Configurer les journaux d'erreurs de l'Agent SQL Server (page Général)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cet écran pour afficher et mettre à jour les paramètres du journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Fichier journal des erreurs**  
Spécifie le nom du fichier dans lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent consigne les erreurs.  
  
**...**  
Permet de parcourir l'arborescence à la recherche du fichier journal des erreurs.  
  
**Écrire dans le fichier journal des erreurs OEM**  
Écrit le fichier journal des erreurs comme un fichier non-Unicode. Cela réduit l'espace disque utilisé par le fichier journal. Toutefois, si vous activez cette option, sachez que les messages incluant des données Unicode peuvent être plus difficiles à lire.  
  
**Erreurs**  
Écrit uniquement les erreurs et les messages d'information dans le fichier journal.  
  
**Avertissements**  
Écrit uniquement les avertissements et les messages d'information dans le fichier journal.  
  
**Informations**  
Écrit uniquement les messages d'information dans le fichier journal.  
  
## <a name="see-also"></a>Voir aussi  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
