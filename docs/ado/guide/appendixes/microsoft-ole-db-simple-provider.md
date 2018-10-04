---
title: Fournisseur Simple Microsoft OLE DB | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bd22d13a0fe656a7d176d6fb9fd2a97e3ce8d3b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673532"
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Vue d’ensemble de la Simple fournisseur Microsoft OLE DB
Le Microsoft OLE DB Simple fournisseur (OSP) permet à ADO d’accéder aux données pour laquelle un fournisseur a été écrite à l’aide de la [Kit de ressources OLE DB Simple fournisseur (OSP)](http://msdn.microsoft.com/6e7b7931-9e4a-4151-ae51-672abd3f84a6). Les fournisseurs de simples sont destinées à accéder aux sources de données qui nécessitent la prise en charge OLE DB uniquement fondamentaux, tels que des tableaux en mémoire ou des documents XML.

## <a name="connection-string-parameters"></a>Paramètres de chaîne de connexion
 Pour vous connecter à la base de données Simple DLL du fournisseur OLE, définissez la *fournisseur* l’argument de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété :

```
MSDAOSP
```

 Cette valeur peut également être définie ou lire à l’aide de la [fournisseur](../../../ado/reference/ado-api/provider-property-ado.md) propriété.

 Vous pouvez vous connecter à des fournisseurs simples qui ont été inscrits en tant que les fournisseurs OLE DB complètes en utilisant le nom de fournisseur inscrit, déterminé par le writer de fournisseur.

## <a name="typical-connection-string"></a>Chaîne de connexion classique
 Une chaîne de connexion classique pour ce fournisseur est :

```
"Provider=MSDAOSP;Data Source=serverName"
```

 La chaîne se compose de ces mots clés :

|Mot clé|Description|
|-------------|-----------------|
|**Fournisseur**|Spécifie le fournisseur OLE DB pour SQL Server.|
|**Source de données**|Spécifie le nom d’un serveur.|

## <a name="xml-document-example"></a>Exemple de Document XML
 Le OLE DB Simple fournisseur (OSP) dans MDAC 2.7 ou version ultérieure et Windows Data Access Components (Windows DAC) a été amélioré pour prendre en charge l’ouverture d’ADO hiérarchique **Recordsets** sur des fichiers XML arbitraires. Ces fichiers XML peuvent contenir le schéma de persistance XML ADO, mais il n’est pas obligatoire. Cela a été implémentée en connectant l’OSP à la **MSXML2.DLL**; par conséquent **MSXML2.DLL** ou ultérieure est requise.

 Le **portfolio.xml** fichier utilisé dans l’exemple suivant contient l’arborescence suivante :

```
Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite
```

 L’objet DSO XML utilise une méthode heuristique pour convertir les nœuds dans une arborescence XML chapitres dans une liste hiérarchique **Recordset**.

 À l’aide de ces heuristiques intégrés, l’arborescence XML est convertie en un deux niveaux hiérarchique **Recordset** sous la forme suivante :

```
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Notez que les balises de portefeuille et les informations ne sont pas représentés dans la liste hiérarchique **Recordset**. Pour une explication de la façon dont l’objet DSO XML convertit arborescences XML hiérarchique **Recordsets**, consultez les règles suivantes. La colonne $Text est abordée dans la section suivante.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Règles d’affectation d’éléments et attributs XML pour les colonnes et lignes
 L’objet DSO XML suit une procédure pour l’affectation d’éléments et attributs aux colonnes et lignes dans les applications lié aux données. XML est modelée comme une arborescence avec une balise qui contient toute la hiérarchie. Par exemple, une description XML d’un livre peut contenir des balises de chapitre, les balises de figure et balises de section. Niveau le plus élevé serait la balise de livre, qui contient la figure, la section et le chapitre de sous-éléments. Lorsque l’objet DSO XML mappe des éléments XML en lignes et colonnes, les sous-éléments, pas l’élément de niveau supérieur, sont convertis.

 L’objet DSO XML utilise cette procédure pour la conversion des sous-éléments :

-   Chaque sous-élément et l’attribut correspondant à une colonne dans certains **Recordset** dans la hiérarchie.

-   Le nom de la colonne est la même que le nom de l’attribut, ou le sous-élément, sauf si l’élément parent possède un attribut et un sous-élément portant le même nom, auquel cas un « ! » est ajouté au nom de colonne du sous-élément.

-   Chaque colonne est soit un *simple* colonne qui contient des valeurs scalaires (généralement des chaînes) ou un **Recordset** colonne qui contient les enfants **Recordsets**.

-   Colonnes qui correspondent aux attributs sont toujours simples.

-   Colonnes qui correspondent à des sous-éléments sont **Recordset** colonnes si le sous-élément a ses propres sous-éléments ou attributs (ou les deux), soit les parents du sous-élément a plusieurs instances du sous-élément en tant qu’enfant. Sinon, la colonne est simple.

-   Lorsqu’il existe plusieurs instances d’un sous-élément (sous des parents différents), sa colonne est un **Recordset** colonne si *n’importe quel* des instances implique un **Recordset** colonne ; son Il suffit de colonne uniquement si *tous les* instances impliquent une colonne simple.

-   Tous les **Recordsets** ont une colonne supplémentaire nommée $Text.

 Le code qui est nécessaire pour construire un **Recordset** se présente comme suit :

```
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "http://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Le chemin d’accès du fichier de données peut être spécifié à l’aide de quatre différentes conventions d’affectation de noms.

```
'HTTP://
adoRS.Open "http://WebServer/VRoot/portfolio.xml", adoConn
'FILE://
adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
'UNC Path
adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
'Full DOS Path
adoRS.Open "C:\Directory\portfolio.xml", adoConn
```

 Dès que le **Recordset** a été ouvert, ADO habituel **Recordset** les commandes de navigation peuvent être utilisées.

 **Jeux d’enregistrements** généré par l’OSP ont quelques limitations :

-   Les curseurs clients (**adUseClient**) ne sont pas pris en charge.

-   Hiérarchique **Recordsets** créés au fil du arbitraire XML ne peut pas être persistante à l’aide de **Recordset.Save**.

-   **Jeux d’enregistrements** créé avec l’OSP sont en lecture seule.

-   Le XMLDSO ajoute une colonne supplémentaire de données ($Text) à chaque **Recordset** dans la hiérarchie.

 Pour plus d’informations sur le fournisseur OLE DB Simple, consultez [création d’un fournisseur Simple](http://msdn.microsoft.com/b31a6cba-58ae-4ee8-9039-700973d354d6).

## <a name="code-example"></a>Exemple de code
 Le code Visual Basic suivant illustre l’ouverture d’un fichier XML arbitraire, en créant une liste hiérarchique **Recordset**et l’écriture de chaque enregistrement de chacun d’eux de manière récursive **Recordset** à la fenêtre de débogage.

 Voici un fichier XML simple qui contient les cotations boursières. Le code suivant utilise ce fichier pour construire un deux niveaux hiérarchique **Recordset**.

```
<portfolio>
   <stock>
      <shares>100</shares>
      <symbol>MSFT</symbol>
      <price>$70.00</price>
      <info>
         <companyname>Microsoft Corporation</companyname>
         <website>http://www.microsoft.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>AAPL</symbol>
      <price>$107.00</price>
      <info>
         <companyname>Apple Computer, Inc.</companyname>
         <website>http://www.apple.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>DELL</symbol>
      <price>$50.00</price>
      <info>
         <companyname>Dell Corporation</companyname>
         <website>http://www.dell.com</website>
      </info>
    </stock>
    <stock>
       <shares>100</shares>
       <symbol>INTC</symbol>
       <price>$115.00</price>
       <info>
          <companyname>Intel Corporation</companyname>
          <website>http://www.intel.com</website>
       </info>
   </stock>
</portfolio>
```

 Voici les deux procédures sub de Visual Basic. La première crée le **Recordset** et le transmet à la *WalkHier* sub, procédure, présente de quelle manière récursive vers le bas de la hiérarchie, chaque écriture **champ** dans chaque enregistrement de chaque **Recordset** à la fenêtre de débogage.

```
Private Sub BrowseHierRecordset()
' Add ADO 2.7 or later to Project/References
' No need to add MSXML2, ADO just passes the ProgID through to the OSP.

    Dim adoConn As ADODB.Connection
    Dim adoRS As ADODB.Recordset
    Dim adoChildRS As ADODB.Recordset

    Set adoConn = New ADODB.Connection
    Set adoRS = New ADODB.Recordset
    Set adoChildRS = ADODB.Recordset

    adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
    adoRS.Open "http://bwillett3/Kowalski/portfolio.xml", adoConn

    Dim iLevel As Integer
    iLevel = 0
    WalkHier iLevel, adoRS

End Sub

Sub WalkHier(ByVal iLevel As Integer, ByVal adoRS As ADODB.Recordset)
    iLevel = iLevel + 1
    PriorLevel = iLevel
    While Not adoRS.EOF
        For ndx = 0 To adoRS.Fields.Count - 1
            If adoRS.Fields(ndx).Name <> "$Text" Then
                If adoRS.Fields(ndx).Type = adChapter Then
                    Set adoChildRS = adoRS.Fields(ndx).Value
                    WalkHier iLevel, adoChildRS
                Else
                    Debug.Print iLevel & ": adoRS.Fields(" & ndx & _
                       ") = " & adoRS.Fields(ndx).Name & " = " & _
                       adoRS.Fields(ndx).Value
                End If
            End If
        Next ndx
        adoRS.MoveNext
    Wend
    iLevel = PriorLevel
End Sub
```
