---
title: 'Leçon 2 : Création d’un abonnement à la publication transactionnelle | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ace792a76e1bcdbcc7aa6b372d96de1f92c570f5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072249"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>Leçon 2 : Création d'un abonnement à la publication transactionnelle
  Dans cette leçon, vous allez créer l'abonnement à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour effectuer cette leçon, vous devez avoir terminé la leçon précédente, [Leçon 1 : Publication de données à l’aide de la réplication transactionnelle](lesson-1-publishing-data-using-transactional-replication.md).  
  
### <a name="to-create-the-subscription"></a>Pour créer l'abonnement  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales** , cliquez avec le bouton droit sur la publication **AdvWorksProductTrans** , puis cliquez sur **Nouveaux abonnements**.  
  
     L'Assistant Nouvel abonnement démarre.  
  
3.  Dans la page Publication, sélectionnez **AdvWorksProductTrans**, puis cliquez sur **Suivant**.  
  
4.  Dans la page Emplacement de l’Agent de distribution, sélectionnez **Exécuter tous les agents sur le serveur de distribution**, puis cliquez sur **Suivant**.  
  
5.  Dans la page Abonnés, si le nom de l’instance de l’Abonné n’apparaît pas, cliquez sur **Ajouter un Abonné**, sur **Ajouter un Abonné SQL Server**, entrez le nom de l’instance de l’Abonné dans la boîte de dialogue **Se connecter au serveur** , puis cliquez sur **Se connecter**.  
  
6.  Dans la page abonnés, sélectionnez le nom de l’instance de l’abonné, puis  **\<nouvelle base de données >** sous **base de données d’abonnement**.  
  
7.  Dans la boîte de dialogue **Nouvelle base de données** , entrez **ProductReplica** dans la zone **Nom de la base de données** , cliquez sur **OK**, puis sur **Suivant**.  
  
8.  Dans la boîte de dialogue **Sécurité de l’Agent de distribution**, cliquez sur le bouton de sélection (**…**), entrez \<*nom_ordinateur>***\repl_distribution** dans la zone **Compte de processus**, tapez le mot de passe du compte, cliquez sur **OK**, puis sur **Suivant**.  
  
9. Cliquez sur **Terminer** pour accepter les valeurs par défaut des pages restantes et terminer l’Assistant.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Définition des autorisations de base de données sur l'Abonné  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez **Bases de données**, **ProductReplica**et **Sécurité**, cliquez avec le bouton droit sur **Utilisateurs**, puis sélectionnez **Nouvel utilisateur**.  
  
2.  Dans la page **Général**, dans la liste **Type d’utilisateur**, sélectionnez **Utilisateur Windows**.  
  
3.  Cochez la case **Nom d’utilisateur** et cliquez sur le bouton (…), dans la zone **Entrez les noms d’objets à sélectionner** entrez <nom_ordinateur>**\repl_distribution**, cliquez sur **Vérifier les noms**, puis cliquez sur **OK**.  
  
4.  Dans la page **Appartenance**, dans la zone **Appartenance au rôle de base de données**, sélectionnez **db_owner**, puis cliquez sur **OK** pour créer l’utilisateur.  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>Pour afficher l'état de synchronisation de l'abonnement  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur et le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales** , développez la publication **AdvWorksProductTrans** , cliquez avec le bouton droit sur l’abonnement dans la base de données **ProductReplica** , puis cliquez sur **Afficher l’état de synchronisation**.  
  
     L'état de synchronisation de l'abonnement s'affiche.  
  
3.  Si l’abonnement n’apparaît pas sous **AdvWorksProductTrans**, appuyez sur F5 pour actualiser la liste.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé avec succès un abonnement à la publication transactionnelle. Comme l'Agent de distribution de cet abonnement s'exécute en permanence, l'abonnement est initialisé lors de sa création. Ensuite, vous allez utiliser les jetons de suivi pour vérifier que les modifications sont bien répliquées sur l'Abonné et pour déterminer la latence. Voir [Leçon 3 : Validation de l’abonnement et mesure de la latence](lesson-3-validating-the-subscription-and-measuring-latency.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
