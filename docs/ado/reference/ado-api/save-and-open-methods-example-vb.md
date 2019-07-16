---
title: Enregistrer et ouvrir des exemples de méthodes (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6d42488f8f167cc7c98f663478c742963d24253c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931195"
---
# <a name="save-and-open-methods-example-vb"></a>Save et Open, exemple de méthodes (VB)
Ces trois exemples montrent comment la [enregistrer](../../../ado/reference/ado-api/save-method.md) et [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthodes peuvent être utilisés ensemble.  
  
 Supposons que vous allez voyage d’affaires et que vous souhaitez effectuer le long d’une table à partir d’une base de données. Avant de passer, vous accéder aux données en tant qu’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) et enregistrez-le dans un format transportable. Lorsque vous arrivez à destination, vous accédez le **Recordset** comme local, déconnecté **Recordset**. Vous apportez des modifications à la **Recordset**, puis enregistrez-le à nouveau. Enfin, lorsque vous revenez accueil, vous reconnecter à la base de données et mettre à jour avec les modifications apportées sur la route.  
  
 Tout d’abord, ouvrir et enregistrer le ***auteurs*** table.  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 À ce stade, vous êtes arrivé à destination. Vous accéderez à la ***auteurs*** table comme local, déconnecté **Recordset**. Vous devez avoir le **MSPersist** fournisseur sur l’ordinateur que vous utilisez pour accéder au fichier enregistré, a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Enfin, vous retournez accueil. Maintenant, mettre à jour la base de données avec vos modifications.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Plus d’informations sur la persistance des recordsets](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
