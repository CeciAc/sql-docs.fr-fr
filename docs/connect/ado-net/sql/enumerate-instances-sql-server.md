---
title: Énumération des instances de SQL Server (ADO.NET)
description: Décrit comment énumérer des instances actives de SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d6c83ffd407a9b27a04b254fb3e9e5673a600417
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452202"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Énumération des instances de SQL Server (ADO.NET)

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server permet aux applications de trouver des instances de SQL Server dans le réseau actuel. La classe <xref:System.Data.Sql.SqlDataSourceEnumerator> expose ces informations au développeur d’applications, en fournissant un <xref:System.Data.DataTable> contenant des informations sur tous les serveurs visibles. Cette table retournée contient une liste des instances de serveur disponibles sur le réseau, qui correspond à celle fournie quand un utilisateur tente de créer une nouvelle connexion et développe la liste déroulante contenant tous les serveurs disponibles dans la boîte de dialogue **Propriétés des connexions**. Les résultats affichés ne sont pas toujours terminés.  
  
> [!NOTE]
>  Comme pour la plupart des services Windows, il est préférable d’exécuter le service SQL Browser avec le moins de privilèges possible. Pour plus d’informations sur le service SQL Browser et sur la manière de gérer son comportement, consultez la Documentation en ligne de SQL Server.  
  
## <a name="retrieving-an-enumerator-instance"></a>Récupération d’une instance d’énumérateur  
Pour extraire la table contenant des informations sur les instances de SQL Server disponibles, vous devez commencer par extraire un énumérateur en utilisant la propriété partagée/statique <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
Une fois que vous avez récupéré l’instance statique, vous pouvez appeler la méthode <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>, qui retourne un <xref:System.Data.DataTable> contenant des informations sur les serveurs disponibles :  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
La table retournée par l’appel de méthode contient les colonnes suivantes, qui contiennent toutes des valeurs de `string` :  
  
|colonne|Description|  
|------------|-----------------|  
|**ServerName**|Nom du serveur.|  
|**InstanceName**|Nom d'instance du serveur. Vide si le serveur s’exécute en tant qu’instance par défaut.|  
|**IsClustered**|Indique si SQL Server fait partie ou non d'un cluster.|  
|**Version**|Version du serveur. Par exemple :<br /><br /> -   9.00.x (SQL Server 2005)<br />SQL Server 10.0 (2008)<br />-   10.50.x (SQL Server 2008 R2)<br />SQL Server 11.0 (2012)|  
  
## <a name="enumeration-limitations"></a>Limitations de l’énumération  
Tous les serveurs disponibles peuvent être ou non listés. La liste peut varier en fonction de facteurs tels que les délais d’attente et le trafic réseau. Cela peut entraîner la différence entre la liste et deux appels consécutifs. Seuls les serveurs sur le même réseau sont listés. En général, les paquets de diffusion ne traversent pas les routeurs, ce qui explique pourquoi vous ne voyez pas un serveur listé, mais il sera stable entre les appels.  
  
Les serveurs listés peuvent contenir des informations supplémentaires, telles que `IsClustered` et la version. Cela dépend de la façon dont la liste a été obtenue. Les serveurs listés à l’aide du service de navigateur de SQL Server offrent plus de détails que ceux trouvés par le biais de l’infrastructure Windows, qui n’indique que le nom.  
  
> [!NOTE]
>  L’énumération de serveur est disponible uniquement lors de l’exécution avec un niveau de confiance totale. Les assemblys qui s’exécutent dans un environnement de confiance partielle ne peuvent pas l’utiliser, même s’ils disposent de l’autorisation <xref:Microsoft.Data.SqlClient.SqlClientPermission> Code Access Security (CAS).  
  
SQL Server fournit des informations pour <xref:System.Data.Sql.SqlDataSourceEnumerator> en utilisant un service Windows externe nommé SQL Browser. Ce service est activé par défaut, mais les administrateurs peuvent le désactiver ou le désactiver, ce qui rend l’instance de serveur invisible pour cette classe.  
  
## <a name="example"></a>Exemple  
L’application console suivante extrait des informations sur toutes les instances de SQL Server visibles et affiche les informations dans la fenêtre de console.  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
