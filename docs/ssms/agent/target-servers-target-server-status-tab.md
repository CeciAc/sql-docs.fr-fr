---
title: Serveurs cibles (onglet État du serveur cible) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.target.status.f1
ms.assetid: 010a4cab-d878-4889-8ac8-7d91db6345d6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 00b908dc1162ea3c0392a2fdaaf48c405a32a9f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805087"
---
# <a name="target-servers-target-server-status-tab"></a>Serveurs cibles (onglet État du serveur cible)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher l'état des serveurs cibles de ce serveur maître.  
  
## <a name="options"></a>Options  
**Serveur cible**  
Affiche le nom du serveur cible.  
  
**Heure locale**  
Affiche la date et l'heure du serveur cible correspondant au fuseau horaire local de ce serveur.  
  
**Dernière interrogation**  
Affiche la date et l'heure locales auxquelles le serveur cible a interrogé pour la dernière fois le serveur maître.  
  
**Instructions non lues**  
Affiche le nombre d'instructions que le serveur cible n'a pas encore reçues.  
  
**État**  
Affiche l'état du serveur cible.  
  
**Forcer l'interrogation**  
Cliquez sur ce bouton pour forcer les serveurs cibles sélectionnés à interroger le serveur maître.  
  
**Forcer la désinscription**  
Cliquez sur ce bouton pour forcer les serveurs cibles sélectionnés à se désinscrire du serveur maître.  
  
**Publier les instructions**  
Publie les instructions sur les serveurs cibles sélectionnés.  
  
**Activer l'actualisation automatique**  
Sélectionnez cette option pour actualiser automatiquement les informations affichées.  
  
**Actualiser toutes les**  
Spécifiez la fréquence à laquelle les informations de cette page doivent être actualisées.  
  
## <a name="see-also"></a> Voir aussi  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
