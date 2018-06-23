---
title: Modifier une session d’événements étendus | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97971c56e6f094d7cf905da0db4475f3703c1416
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043598"
---
# <a name="alter-an-extended-events-session"></a>Modifier une session d'événements étendus
  Après avoir créé une session d'événements étendus, vous pouvez la modifier en fonction de vos besoins à l'aide de l' **Assistant Événements étendus SQL Server**.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Vous ne pouvez pas modifier une cible pour les sessions actives et inactives, et vous ne pouvez pas modifier les configurations avancées de propriétés pour une session active.  
  
 Vous pouvez apporter les modifications suivantes aux sessions d'événements actives et inactives :  
  
-   Ajouter ou supprimer des événements de la session, puis modifier les configurations des événements, telles que les champs d'événement, les filtres et les actions.  
  
-   Ajouter ou supprimer une cible de la session d'événements.  
  
-   Activer l'option **Démarrer la session d'événements au démarrage du serveur** .  
  
 Vous pouvez apporter les modifications supplémentaires suivantes à une session d'événements inactive :  
  
-   Activer l'option **Suivre la relation entre les événements** .  
  
-   Modifier la configuration de propriétés avancée.  
  
> [!NOTE]  
>  L’ **Assistant Événements étendus SQL Server** ne prend pas en charge la modification de la session d’événements.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Comment modifier une session d'événements étendus à l'aide de l'Assistant Événements étendus SQL Server  
  
-   Dans l'Explorateur d'objets, développez **Gestion**, **Événements étendus**, puis **Sessions**.  
  
-   Cliquez avec le bouton droit sur la session à modifier, puis cliquez sur **Propriétés**.  
  
-   Dans la boîte de dialogue **Propriétés** , apportez les modifications appropriées, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [Créer une session d'événements étendus à l'aide de l'éditeur de requête](../../database-engine/create-an-extended-events-session-using-query-editor.md)  
  
  
