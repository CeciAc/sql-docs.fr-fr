---
title: Opérations asynchrones
description: Décrit comment effectuer des opérations de base de données asynchrones à l’aide d’une API modélisée d’après le modèle asynchrone utilisé par le .NET Framework.
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 79cde936328476408fabb3df7a6bff8d983ace1c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452325"
---
# <a name="asynchronous-operations"></a>Opérations asynchrones

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Certaines opérations de base de données, telles que les exécutions de commande, peuvent prendre beaucoup de temps. Dans ce cas, les applications à thread unique doivent bloquer d'autres opérations et attendre que la commande ait terminé avant de poursuivre les autres opérations. En revanche, pouvoir affecter une opération longue à un thread d’arrière-plan permet au thread de premier plan de rester actif pendant l’opération. Dans une application Windows, par exemple, la délégation de l’opération de longue durée à un thread d’arrière-plan permet au thread d’interface utilisateur de rester réactif pendant l’exécution de l’opération.  
  
.NET fournit plusieurs modèles de design asynchrone standard que les développeurs peuvent utiliser pour tirer parti des threads d’arrière-plan et libérer l’interface utilisateur ou des threads de haute priorité pour effectuer d’autres opérations dans sa classe <xref:Microsoft.Data.SqlClient.SqlCommand>. Plus précisément, les méthodes <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> et <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, associées aux méthodes <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> et <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A>, fournissent la prise en charge asynchrone.  
  
> [!NOTE]
>  La programmation asynchrone est une fonctionnalité principale de .NET. Pour plus d’informations sur les différentes techniques asynchrones disponibles pour les développeurs, consultez [appel de méthodes synchrones de façon asynchrone](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously).  
  
Bien que l’utilisation de techniques asynchrones avec des fonctionnalités ADO.NET n’ajoute pas de considérations spéciales, il est important d’être conscient des avantages et des pièges liés à la création d’applications multithread. Les exemples qui suivent dans cette section signalent plusieurs problèmes importants que les développeurs doivent prendre en compte lors de la création d’applications qui incorporent des fonctionnalités multithread.  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Applications Windows utilisant des rappels](windows-applications-callbacks.md)  
Fournit un exemple montrant comment exécuter une commande asynchrone en toute sécurité, en gérant correctement l’interaction avec un formulaire et son contenu à partir d’un thread distinct.  
  
[Applications ASP.NET utilisant des handles d’attente](aspnet-apps-use-wait-handles.md)  
Fournit un exemple montrant comment exécuter plusieurs commandes simultanées à partir d’une page ASP.NET, à l’aide de handles d’attente pour gérer l’opération à l’achèvement de toutes les commandes.  
  
[Interrogation dans les applications console](poll-console-applications.md)  
Fournit un exemple illustrant l’utilisation de l’interrogation pour attendre la fin de l’exécution d’une commande asynchrone à partir d’une application console. Cette technique est également valide dans une bibliothèque de classes ou une autre application sans interface utilisateur.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
- [Appel asynchrone de méthodes synchrones](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
