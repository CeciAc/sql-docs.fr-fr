---
title: Configurer la messagerie de l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données
ms.custom: seo-dt-2019
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0692421ca7e63b419c99ecc835516af4cbd5af0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74095780"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Configurer la messagerie de l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment configurer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser la messagerie de base de données pour envoyer une notification et des alertes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Pour plus d’informations sur l’activation et la configuration de la messagerie de base de données, consultez [Configurer la messagerie de base de données](../../relational-databases/database-mail/configure-database-mail.md).  Pour obtenir un exemple faisant appel à [!INCLUDE[tsql](../../includes/tsql-md.md)][Créer un profil de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-profile.md)
  
-   **Avant de commencer :**  
  
-   [Prérequis](#Prerequisites)  
  
-   [Sécurité](#Security)  
  
-   [Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données, à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
-   [Tâches de suivi](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
  > [!NOTE]
  > L’agent SQL sur Managed Instance est toujours configuré pour utiliser Database Mail. Ce contenu ne s’applique donc pas à Managed Instance. Dans Managed Instance, vous devez avoir un profil appelé **[AzureManagedInstance_dbmail_profile](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)** pour lier l’agent SQL à Database Mail. 
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   [Activer la messagerie de base de données](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md) pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser.  
  
-   [Créer un profil de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-profile.md) pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser, et ajouter l’utilisateur au rôle **DatabaseMailUserRole** de la base de données **msdb** .
  
-   Définir le profil comme profil par défaut pour la base de données **msdb** .  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L'utilisateur qui crée les comptes de profils et exécute des procédures stockées doit être membre du rôle serveur fixe sysadmin.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données**  
  
-   Dans l'Explorateur d'objets, développez une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
-   Cliquez sur **Système d'alerte**.  
  
-   Sélectionnez **Activer le profil de messagerie**.  
  
-   Dans la liste **Système de messagerie** , choisissez **Database Mail**.  
  
-   Dans la liste **Profil de la messagerie**, sélectionnez un profil de messagerie pour la messagerie de base de données. 
  
-   Redémarrez SQL Server Agent.  
  
##  <a name="Follow_Up"></a> Tâches de suivi  
 Les tâches suivantes sont nécessaires pour terminer la configuration de l'Agent pour envoyer des alertes et des notifications.  
  
-   [Alertes](../../ssms/agent/alerts.md)  
  
     Les alertes peuvent être configurées pour notifier à un opérateur une situation du système d'exploitation ou un événement de base de données particuliers.  
  
-   [Opérateurs](../../ssms/agent/operators.md)  
  
     Les opérateurs sont des alias pour les personnes ou les groupes qui peuvent recevoir une notification électronique  
  
  
