---
title: Statistiques du fournisseur pour SQL Server
description: Décrit la prise en charge de l’obtention de statistiques d’exécution SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 092cf63e62bce01e2a771ce4e5f7f46e1073e91a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452063"
---
# <a name="provider-statistics-for-sql-server"></a>Statistiques du fournisseur pour SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

À partir de la version 2,0 de .NET Framework et de .NET Core version 1,0, le Fournisseur de données Microsoft SqlClient pour SQL Server prend en charge les statistiques d’exécution. Vous devez activer les statistiques en affectant à la propriété <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> de l’objet <xref:Microsoft.Data.SqlClient.SqlConnection> la valeur `True` une fois que vous avez créé un objet de connexion valide. Une fois les statistiques activées, vous pouvez les examiner comme un « instantané dans le temps » en extrayant une référence <xref:System.Collections.IDictionary> via la méthode <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> de l’objet <xref:Microsoft.Data.SqlClient.SqlConnection>. Vous énumérez la liste sous la forme d’un ensemble d’entrées de dictionnaire de paires nom/valeur. Ces paires nom/valeur ne sont pas ordonnées. À tout moment, vous pouvez appeler la méthode <xref:Microsoft.Data.SqlClient.SqlConnection.ResetStatistics%2A> de l’objet <xref:Microsoft.Data.SqlClient.SqlConnection> pour réinitialiser les compteurs. Si la collecte de statistiques n’a pas été activée, aucune exception n’est générée. En outre, si <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> est appelée sans <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ayant été appelée en premier, les valeurs récupérées sont les valeurs initiales de chaque entrée. Si vous activez les statistiques, exécutez votre application pendant un certain temps, puis désactivez les statistiques, les valeurs récupérées reflètent les valeurs collectées jusqu’au point où les statistiques ont été désactivées. Toutes les valeurs statistiques rassemblées sont basées pour chaque connexion.  
  
## <a name="statistical-values-available"></a>Valeurs statistiques disponibles  
Actuellement, il existe 18 éléments différents disponibles auprès du fournisseur Microsoft SQL Server. Le nombre d’éléments disponibles est accessible par le biais de la propriété **Count** de la référence d’interface <xref:System.Collections.IDictionary> retournée par <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Tous les compteurs relatifs aux statistiques de fournisseur utilisent le type Common Language Runtime <xref:System.Int64> (**long** en C# et Visual Basic), dont la taille est de 64 bits. La valeur maximale du type de données **int64**, telle que définie par le champ **int64.MaxValue**, est ((2^63)-1)). Lorsque les valeurs des compteurs atteignent cette valeur maximale, elles ne doivent plus être considérées comme exactes. Cela signifie que **int64.MaxValue**-1((2^63)-2) est effectivement la valeur valide la plus élevée pour toute statistique.  
  
> [!NOTE]
>  Un dictionnaire est utilisé pour retourner les statistiques du fournisseur, car le nombre, le nom et l’ordre des statistiques retournées peuvent changer à l’avenir. Les applications ne doivent pas s’appuyer sur une valeur spécifique trouvée dans le dictionnaire, mais doivent à la place vérifier si la valeur existe et créer une branche en conséquence.  
  
Le tableau suivant décrit les valeurs statistiques actuelles disponibles. Notez que les noms de clés pour les valeurs individuelles ne sont pas localisés dans les versions régionales de l’infrastructure Microsoft .NET et .NET Core.  
  
|Nom de la clé|Description|  
|--------------|-----------------|  
|`BuffersReceived`|Retourne le nombre de paquets tabular data stream (TDS) reçus par le fournisseur à partir de SQL Server après que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`BuffersSent`|Retourne le nombre de paquets TDS envoyés à SQL Server par le fournisseur une fois que les statistiques ont été activées. Les commandes de grande taille peuvent nécessiter plusieurs mémoires tampons. Par exemple, si une commande de grande taille est envoyée au serveur et nécessite six paquets, `ServerRoundtrips` est incrémenté d’une unité et `BuffersSent` est incrémenté de six.|  
|`BytesReceived`|Retourne le nombre d’octets de données dans les paquets TDS reçus par le fournisseur à partir de SQL Server une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`BytesSent`|Retourne le nombre d’octets de données envoyés à SQL Server dans les paquets TDS une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`ConnectionTime`|La durée (en millisecondes) pendant laquelle les connexions ont été ouvertes après que les statistiques ont été activées (temps de connexion total si les statistiques ont été activées avant l’ouverture de la connexion).|  
|`CursorOpens`|Retourne le nombre de fois qu’un curseur a été ouvert via la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.<br /><br /> Notez que les résultats en lecture seule/en avant uniquement retournés par les instructions SELECT ne sont pas considérés comme des curseurs et n’affectent donc pas ce compteur.|  
|`ExecutionTime`|Retourne la durée cumulée (en millisecondes) que le fournisseur a consacré au traitement une fois les statistiques activées, y compris le temps passé à attendre des réponses du serveur, ainsi que le temps passé à exécuter du code dans le fournisseur proprement dit.<br /><br /> Les classes qui incluent le code de minutage sont les suivantes :<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Pour maintenir le plus petit possible les membres critiques en matière de performances, les membres suivants ne sont pas chronométrés :<br /><br /> SqlDataReader<br /><br /> This [], opérateur (toutes les surcharges)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Retourne le nombre total d’instructions INSERT, DELETE et UPDATE exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`IduRows`|Retourne le nombre total de lignes affectées par les instructions INSERT, DELETE et UPDATE exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`NetworkServerTime`|Retourne la durée cumulée (en millisecondes) que le fournisseur a passé à attendre des réponses du serveur après que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`PreparedExecs`|Retourne le nombre de commandes préparées exécutées par le biais de la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`Prepares`|Retourne le nombre d’instructions préparées par le biais de la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`SelectCount`|Retourne le nombre d’instructions SELECT exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques. Cela comprend les instructions FETCH permettant d’extraire des lignes de curseurs, et le nombre d’instructions SELECT est mis à jour lorsque la fin d’un <xref:Microsoft.Data.SqlClient.SqlDataReader> est atteinte.|  
|`SelectRows`|Retourne le nombre de lignes sélectionnées une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques. Ce compteur reflète toutes les lignes générées par les instructions SQL, même celles qui n’ont pas été réellement consommées par l’appelant. Par exemple, la fermeture d’un lecteur de données avant la lecture du jeu de résultats entier n’affecte pas le nombre. Cela comprend les lignes extraites des curseurs à l’aide d’instructions FETCH.|  
|`ServerRoundtrips`|Retourne le nombre de fois que la connexion a envoyé des commandes au serveur et a obtenu une réponse une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
|`SumResultSets`|Retourne le nombre de jeux de résultats qui ont été utilisés une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques. Par exemple, cela inclut tous les jeux de résultats renvoyés au client. Pour les curseurs, chaque opération d’extraction ou de récupération de bloc est considérée comme un jeu de résultats indépendant.|  
|`Transactions`|Retourne le nombre de transactions utilisateur démarrées une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques, y compris les restaurations. Si une connexion est en cours d’exécution avec la validation automatique sur, chaque commande est considérée comme une transaction.<br /><br /> Ce compteur incrémente le nombre de transactions dès qu’une instruction BEGIN TRAN est exécutée, que la transaction soit validée ou annulée ultérieurement.|  
|`UnpreparedExecs`|Retourne le nombre d’instructions qui ne sont pas préparées exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et a activé les statistiques.|  
  
### <a name="retrieving-a-value"></a>Récupération d’une valeur  
L’application console suivante montre comment activer les statistiques sur une connexion, récupérer quatre valeurs de statistiques individuelles et les écrire dans la fenêtre de console.  
  
> [!NOTE]
>  L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server. La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local. Modifiez la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Récupération de toutes les valeurs  
L’application console suivante montre comment activer les statistiques sur une connexion, récupérer toutes les valeurs statistiques disponibles à l’aide de l’énumérateur et les écrire dans la fenêtre de console.  
  
> [!NOTE]
>  L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server. La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local. Modifiez la chaîne de connexion en fonction des besoins de votre environnement.  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
