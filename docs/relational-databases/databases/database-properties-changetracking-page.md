---
title: Propriétés de la base de données (page Suivi des modifications) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9cdd4fba26cf337647f0afa5ace87ea04e54c136
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750897"
---
# <a name="database-properties-changetracking-page"></a>Propriétés de la base de données (page Suivi des modifications)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Utilisez cette page pour consulter ou modifier les paramètres de suivi des modifications pour la base de données sélectionnée. Pour plus d’informations sur les options disponibles sur cette page, consultez [Activer et désactiver le suivi des modifications &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>Options  
 **Suivi des modifications**  
 Utilisez cette option pour activer ou désactiver le suivi des modifications pour la base de données.  
  
 Pour activer le suivi des modifications, vous devez posséder l'autorisation de modifier la base de données.  
  
 L’affectation de la valeur **True** définit une option de base de données qui permet d’activer le suivi des modifications sur des tables individuelles.  
  
 Vous pouvez également configurer le suivi des modifications en utilisant [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 **Période de rétention**  
 Spécifie la période minimale de conservation des informations de suivi des modifications dans la base de données. Les données sont supprimées uniquement si la valeur **Nettoyage automatique** a la valeur **True**.  
  
 La valeur par défaut est 2.  
  
 **Unités de la période de rétention**  
 Spécifie les unités de la valeur Période de rétention. Vous avez le choix entre les unités suivantes : **Jours**, **Heures**ou **Minutes**. La valeur par défaut est **Jours**.  
  
 La période de rétention minimale est 1 minute. Il n'existe pas de période de rétention maximale.  
  
 **Nettoyage automatique**  
 Indique si les informations de suivi des modifications sont supprimées automatiquement à l'issue de la période de rétention spécifiée.  
  
 L’activation de l’option **Nettoyage automatique** remplace toute période de rétention personnalisée précédente par la période de rétention par défaut de 2 jours.  
  
## <a name="see-also"></a> Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
