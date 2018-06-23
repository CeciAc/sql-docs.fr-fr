---
title: À l’aide de chargement en masse SQLXML dans l’environnement .NET | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f597ddc37d61337bd60714afbcb564c87c6747f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044211"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a>Utilisation du chargement en masse SQLXML dans l'environnement .NET
  Cette rubrique explique comment exploiter la fonctionnalité de chargement en masse XML dans l'environnement .NET. Pour plus d’informations sur le chargement en masse XML, consultez [exécution de chargement de XML des données en bloc &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).  
  
 Pour utiliser l'objet COM de chargement en masse SQLXML depuis un environnement managé, vous devez ajouter une référence de projet à ce même objet. Ceci génère une interface de wrapper managé autour de l'objet COM de chargement en masse.  
  
> [!NOTE]  
>  Le chargement en masse XML managé ne fonctionne pas avec les flux managés et nécessite l'intervention d'un wrapper autour des flux natifs. Le composant de chargement en masse SQLXML ne s'exécutera pas dans un environnement multithread (attribut '[MTAThread]'). Si vous essayez d’exécuter le composant de chargement en masse dans un environnement multithread, vous obtenez une exception InvalidCastException avec les informations supplémentaires suivantes : « Échec de QueryInterface pour l’interface SQLXMLBULKLOADLib.ISQLXMLBulkLoad ». La solution de contournement consiste à rendre l’objet qui contient le chargement en masse objet thread unique accessible (par exemple, à l’aide de la **[STAThread]** comme indiqué dans l’exemple d’attribut).  
  
 Cette rubrique propose un exemple d'application C# fonctionnel pour les données XML de chargement en masse dans la base de données. Pour créer un exemple fonctionnel, procédez comme suit :  
  
1.  Créez les tables suivantes :  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  Enregistrez le schéma suivant dans un fichier (schema.xml) :  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Enregistrez l'exemple de document XML suivant dans un fichier (data.xml) :  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  Démarrez Visual Studio.  
  
5.  Créez une application console C#.  
  
6.  À partir de la **projet** menu, sélectionnez **ajouter une référence**.  
  
7.  Dans le **COM** onglet, sélectionnez **bibliothèque de types Microsoft SQLXML Bulkload 4.0** (xblkld4.dll) et cliquez sur **OK**. Vous verrez la **Interop.SQLXMLBULKLOADLib** assembly créé dans le projet.  
  
8.  Remplacez la méthode Main() par le code ci-dessous. Mise à jour la **ConnectionString** propriété et le chemin d’accès de fichier pour les fichiers de schéma et les données.  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. Pour charger le code XML dans la table que vous avez créée, créez et exécutez le projet.  
  
    > [!NOTE]  
    >  La référence au composant de chargement en masse (xblkld4.dll) peut également être ajoutée à l'aide de l'outil tlbimp.exe disponible dans le cadre de l'infrastructure .NET. Cet outil crée un wrapper managé pour la DLL native (xblkld4.dll) qui peut être utilisé ensuite dans tous les projets .NET. Exemple :  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     Cet exemple crée la DLL de wrapper managé (SQLXMLBULKLOADLib.dll) que vous pouvez utiliser dans le projet .NET Framework. Dans le .NET Framework, vous ajoutez une référence de projet à toutes les nouvelles DLL que vous créez.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectuer le chargement en masse des données XML &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  