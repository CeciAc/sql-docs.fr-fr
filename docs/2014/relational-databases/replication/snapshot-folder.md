---
title: Dossier d’instantanés | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 15d9b418efba107afad627159450ce45e08da94e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296549"
---
# <a name="snapshot-folder"></a>Dossier d'instantanés
  La page **Dossier d'instantanés** figure dans l'Assistant Configuration de la distribution et l'Assistant Nouvelle publication. L'emplacement que vous définissez pour le dossier d'instantanés est utilisé par défaut pour tous les serveurs de publication activés dans cet Assistant (le dossier par défaut des instantanés ne s'applique pas aux serveurs de publication qui sont ensuite activés dans la boîte de dialogue **Propriétés du serveur de distribution** ). Vous pouvez changer ce dossier par défaut pour n'importe quel serveur de publication dans la page **Serveurs de publication** de l'Assistant Configuration de la distribution ou la boîte de dialogue **Propriétés du serveur de distribution** .  
  
 Le dossier d'instantanés correspond à un simple répertoire que vous définissez sous la forme d'un partage ; les agents qui lisent et écrivent dans le dossier doivent disposer des autorisations suffisantes pour pouvoir y accéder. Pour plus d’informations sur une sécurisation appropriée du dossier, consultez [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md). Avant d'implémenter la réplication, vérifiez que les agents de réplication peuvent se connecter au dossier d'instantanés. Connectez-vous sous le compte qu'utilisera chaque agent et essayez ensuite d'accéder au dossier d'instantanés.  
  
## <a name="options"></a>Options  
 **Snapshot folder**  
 Entrez le chemin d'accès au dossier où vous souhaitez stocker les fichiers d'instantanés.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser un partage réseau comme emplacement pour le dossier d'instantanés. Les chemins locaux (ceux qui commencent par une lettre de lecteur, tel que C:\\) ne sont pas accessibles aux agents sur les autres ordinateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](alternate-snapshot-folder-locations.md)   
 [Configurer la distribution](configure-distribution.md)   
 [Configurer la publication et la distribution](configure-publishing-and-distribution.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)  
  
  
