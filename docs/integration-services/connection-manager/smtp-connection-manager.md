---
title: Gestionnaire de connexions SMTP | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.smtpconnection.f1
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 40e6fc7d5156ebb56266977bf929242db232e3e8
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298490"
---
# <a name="smtp-connection-manager"></a>Gestionnaire de connexions SMTP

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions SMTP permet à un package de se connecter à un serveur SMTP (Simple Mail Transfer Protocol). La tâche Envoyer un message incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise un gestionnaire de connexions SMTP.  
  
 Lorsque vous utilisez Microsoft Exchange comme serveur SMTP, vous pouvez être amené à configurer le gestionnaire de connexions SMTP de manière à utiliser l'authentification Windows. Les serveurs Exchange peuvent être configurés pour ne pas autoriser les connexions SMTP non authentifiées.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Configuration du gestionnaire de connexions SMTP  
 Quand vous ajoutez un gestionnaire de connexions SMTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion SMTP au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** du package. La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **SMTP**.  
  
 Vous pouvez configurer un gestionnaire de connexions SMTP de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion.  
  
-   Indiquez le nom d'un serveur SMTP.  
  
-   Spécifiez la méthode d'authentification à utiliser.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
-   Permet d'indiquer si les communications doivent être chiffrées à l'aide de SSL (Secure Sockets Layer) lors de l'envoi de messages électroniques.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions SMTP](../../integration-services/connection-manager/smtp-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="smtp-connection-manager-editor"></a>Éditeur du gestionnaire de connexions SMTP
  Utilisez la boîte de dialogue **Éditeur du gestionnaire de connexions SMTP** pour spécifier un serveur SMTP (Simple Mail Transfer Protocol).  
  
 Pour en savoir plus sur le gestionnaire de connexions SMTP, consultez [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
### <a name="options"></a>Options  
 **Name**  
 Donnez un nom unique au gestionnaire de connexions.  
  
 **Description**  
 Décrivez le gestionnaire de connexions. Il est recommandé d'indiquer ici l'usage auquel le gestionnaire de connexions est destiné, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Serveur SMTP**  
 Indiquez le nom du serveur SMTP.  
  
 **Utiliser l'authentification Windows**  
 Sélectionnez cette option pour envoyer des messages au moyen d'un serveur SMTP utilisant l'authentification Windows pour authentifier l'accès au serveur.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
> [!NOTE]  
>  Si vous utilisez Microsoft Exchange comme serveur SMTP, vous devrez peut-être définir **Utiliser l'authentification Windows** à **True**. Les serveurs Exchange peuvent être configurés de manière à interdire les connexions SMTP non authentifiées.  
  
 **Activer SSL (Secure Sockets Layer)**  
 Sélectionnez cette option pour chiffrer la communication au moyen de Secure Sockets Layer (SSL) lors de l'envoi de messages électroniques.  
  
