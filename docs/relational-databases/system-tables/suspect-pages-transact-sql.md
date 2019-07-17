---
title: suspect_pages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- suspect_page_table
- suspect_page_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- suspect_pages system table
- suspect pages [SQL Server]
ms.assetid: 119c8d62-eea8-44fb-bf72-de469c838c50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 70dffcbf2ac3eac13f7ef42e901c4fcd99dce769
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130548"
---
# <a name="suspectpages-transact-sql"></a>suspect_pages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par page qui a échoué avec une erreur 823 mineure ou une erreur 824. Les pages sont répertoriées dans cette table lorsqu'elles sont susceptibles de présenter un défaut, mais elles peuvent être correctes en réalité. Une page suspecte est réparée, son état est mis à jour dans le **event_type** colonne.  
  
 Le tableau suivant, qui a une limite de 1 000 lignes, est stocké dans le **msdb** base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**Int**|ID de la base de données à laquelle cette page s'applique.|  
|**file_id**|**int**|ID du fichier dans la base de données.|  
|**page_id**|**bigint**|ID de la page suspecte. Chaque page possède un ID de page qui est une valeur de 32 bits identifiant l'emplacement de la page dans la base de données. Le **page_id** correspond au décalage dans le fichier de données de la page de 8 Ko. Chaque ID de page est unique dans un fichier.|  
|**event_type**|**int**|Type d'erreur :<br /><br /> 1 = Une erreur 823 à l'origine d'une page suspecte (par exemple, une erreur disque) ou une erreur 824 autre qu'une somme de contrôle incorrecte ou une page endommagée (par exemple, un ID de page erroné).<br /><br /> 2 = Somme de contrôle incorrecte.<br /><br /> 3 = Page endommagée.<br /><br /> 4 = Restaurée (la page a été restaurée après avoir été signalée comme étant incorrecte).<br /><br /> 5 = Réparée (DBCC a réparé la page).<br /><br /> 7 = Libérée par DBCC.|  
|**error_count**|**int**|Nombre d'occurrences de l'erreur.|  
|**last_update_date**|**datetime**|Horodatage de la dernière mise à jour.|  
  
## <a name="permissions"></a>Autorisations  
 Toute personne ayant accès à **msdb** peut lire les données de la table **suspect_pages** . Toute personne ayant l'autorisation UPDATE sur la table suspect_pages peut mettre à jour ses enregistrements. Les membres du rôle de base de données fixe **db_owner** sur **msdb** ou du rôle serveur fixe **sysadmin** peuvent insérer, mettre à jour et supprimer des enregistrements.  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer des pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [Classe d’événements de Page de données suspecte de base de données](../../relational-databases/event-classes/database-suspect-data-page-event-class.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
