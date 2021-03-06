---
title: Détection des changements avec SqlDependency
description: Montre comment détecter si les résultats de la requête sont différents de ceux qui ont été reçus à l’origine.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 2d2c4c48a9085fa83d6104233be5f2e1c6b11318
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452246"
---
# <a name="detecting-changes-with-sqldependency"></a>Détection des changements avec SqlDependency

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Un objet <xref:Microsoft.Data.SqlClient.SqlDependency> peut être associé à un <xref:Microsoft.Data.SqlClient.SqlCommand> afin de détecter si les résultats de la requête diffèrent de ceux qui sont récupérés à l’origine. Vous pouvez également assigner un délégué à l’événement `OnChange`, qui se déclenche lorsque les résultats changent pour une commande associée. Vous devez associer le <xref:Microsoft.Data.SqlClient.SqlDependency> à la commande avant d’exécuter la commande. La propriété `HasChanges` du <xref:Microsoft.Data.SqlClient.SqlDependency> peut également être utilisée pour déterminer si les résultats de la requête ont changé depuis la première récupération des données.

## <a name="security-considerations"></a>Considérations relatives à la sécurité

L’infrastructure de dépendance repose sur un <xref:Microsoft.Data.SqlClient.SqlConnection> qui est ouvert lorsque <xref:Microsoft.Data.SqlClient.SqlDependency.Start%2A> est appelé pour recevoir des notifications de modification des données sous-jacentes pour une commande donnée. La possibilité pour un client d’initier l’appel à `SqlDependency.Start` est contrôlée par le biais de l’utilisation d' <xref:Microsoft.Data.SqlClient.SqlClientPermission> et des attributs de sécurité d’accès du code. Pour plus d’informations, consultez [activation des notifications de requête](enable-query-notifications.md).

### <a name="example"></a>Exemple

Les étapes suivantes montrent comment déclarer une dépendance, exécuter une commande et recevoir une notification lorsque le jeu de résultats change :

1. Établit une connexion `SqlDependency` au serveur.

2. Créez <xref:Microsoft.Data.SqlClient.SqlConnection> et <xref:Microsoft.Data.SqlClient.SqlCommand> objets pour vous connecter au serveur et définir une instruction Transact-SQL.

3. Créez un objet `SqlDependency` ou utilisez un objet existant, puis liez-le à l’objet `SqlCommand`. En interne, cela crée un objet <xref:Microsoft.Data.Sql.SqlNotificationRequest> et le lie à l’objet de commande en fonction des besoins. Cette demande de notification contient un identificateur interne qui identifie de façon unique cet objet `SqlDependency`. Il démarre également l’écouteur client s’il n’est pas déjà actif.

4. Abonnez un gestionnaire d’événements à l’événement `OnChange` de l’objet `SqlDependency`.

5. Exécutez la commande à l’aide de l’une des méthodes `Execute` de l’objet `SqlCommand`. Étant donné que la commande est liée à l’objet de notification, le serveur reconnaît qu’il doit générer une notification et les informations de la file d’attente pointent vers la file d’attente des dépendances.

6. Arrêtez la connexion `SqlDependency` au serveur.

Si un utilisateur modifie ensuite les données sous-jacentes, Microsoft SQL Server détecte qu’il existe une notification en attente pour une telle modification et publie une notification qui est traitée et transférée au client via le `SqlConnection` sous-jacent qui a été créé par appel de `SqlDependency.Start`. L’écouteur client reçoit le message d’invalidation. L’écouteur client localise ensuite l’objet `SqlDependency` associé et déclenche l’événement `OnChange`.

Le fragment de code suivant montre le modèle de conception que vous utiliseriez pour créer un exemple d’application.

```csharp
void Initialization()
{
    // Create a dependency connection.
    SqlDependency.Start(connectionString, queueName);
}

void SomeMethod()
{
    // Assume connection is an open SqlConnection.

    // Create a new SqlCommand object.
    using (SqlCommand command=new SqlCommand(
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",
        connection))
    {

        // Create a dependency and associate it with the SqlCommand.
        SqlDependency dependency=new SqlDependency(command);
        // Maintain the reference in a class member.

        // Subscribe to the SqlDependency event.
        dependency.OnChange+=new
           OnChangeEventHandler(OnDependencyChange);

        // Execute the command.
        using (SqlDataReader reader = command.ExecuteReader())
        {
            // Process the DataReader.
        }
    }
}

// Handler method
void OnDependencyChange(object sender,
   SqlNotificationEventArgs e )
{
  // Handle the event (for example, invalidate this cache entry).
}

void Termination()
{
    // Release the dependency.
    SqlDependency.Stop(connectionString, queueName);
}
```

## <a name="next-steps"></a>Étapes suivantes
- [Notifications de requête dans SQL Server](query-notifications-sql-server.md)
