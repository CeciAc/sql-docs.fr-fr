---
title: Propriétés de la publication, Instantané | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.snapshotformat.f1
ms.assetid: 8e9133b1-fc37-4a85-8a7c-d5eaf172fbef
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fbe678e1cb6e89d366a6f39cc0ab44ee9751e5d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706650"
---
# <a name="publication-properties-snapshot"></a>Propriétés de la publication, Instantané
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La page **Instantané** de la boîte de dialogue **Propriétés de la publication** permet de définir un format d'instantané, l'emplacement d'un dossier d'instantanés et des scripts avant et après l'application d'instantané. Le dossier d'instantanés doit être défini comme partage et disposer des autorisations suffisantes pour les agents qui lisent et écrivent des fichiers dans le dossier. Pour plus d’informations sur une sécurisation appropriée du dossier, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
> [!NOTE]  
>  Les modifications nécessitent un nouvel instantané pour la publication. Pour plus d’informations, consultez [Modifier les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## <a name="options"></a>Options  
 **Format d'instantané**  
 Sélectionnez le mode natif ou le mode caractère pour le format d'instantané.  
  
-   Sélectionnez **SQL Server natif - tous les Abonnés doivent être des serveurs qui exécutent SQL Server** si tous les abonnés sont des instances de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autres que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Le format natif d'instantané fournit les meilleures performances.  
  
-   Sélectionnez **Caractère - obligatoire si un serveur de publication ou un Abonné n'exécute pas SQL Server** si des abonnés exécutent [!INCLUDE[ssEW](../../includes/ssew-md.md)] ou sont des abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Emplacement des fichiers d'instantané**  
 Sélectionnez l'emplacement des fichiers d'instantané. Vous pouvez les stocker dans l'emplacement par défaut et dans un emplacement différent, ou seulement dans un emplacement différent. Les fichiers stockés dans un emplacement différent peuvent être compressés.  
  
-   Sélectionnez **Placer les fichiers dans le dossier par défaut** pour utiliser le dossier d'instantanés du serveur de publication. L'emplacement du dossier d'instantanés est en lecture seule dans cette boîte de dialogue, car il ne peut être changé que dans la boîte de dialogue **Propriétés du serveur de distribution** du serveur de publication. Pour plus d’informations, consultez [Spécifier l’emplacement par défaut des instantanés &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
-   Sélectionnez **Placer les fichiers dans le dossier suivant** pour remplacer l'emplacement par défaut ou ajouter un emplacement. Tapez le chemin d'accès dans la zone de texte ou cliquez sur **Parcourir** et accédez à un emplacement. Sélectionnez **Compresser les fichiers d'instantanés dans ce dossier** pour compresser les fichiers dans l'autre emplacement d'instantanés. L'emplacement secondaire peut se trouver sur un autre serveur, un lecteur réseau ou un support amovible (tel qu'un CD-ROM ou un disque amovible). Pour plus d'informations, consultez [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md) et [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md).  
  
 **Exécuter des scripts supplémentaires**  
 Définissez les scripts à exécuter avant et après l'application de l'instantané au niveau de l'Abonné. Vous ne pouvez pas définir de scripts si le **format d'instantané** est **Caractère**.  
  
 Les scripts sont facultatifs, mais ils fournissent une méthode simple pour exécuter des commandes et appliquer des modifications administratives au niveau des abonnés. Pour plus d’informations sur l’exécution des scripts, consultez [Exécuter des scripts avant et après l’application de l’instantané](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Entrez un chemin dans la zone de texte **Exécuter ce script avant l'application de l'instantané** ou cliquez sur **Parcourir** pour définir l'emplacement du script.  
  
-   Entrez un chemin dans la zone de texte **Exécuter ce script après l'application de l'instantané** ou cliquez sur **Parcourir** pour définir l'emplacement du script.  
  
## <a name="see-also"></a> Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Créer et appliquer l’instantané initial](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
