---
title: Collection de paramètres, exemple de commande de propriété (VB) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Command property [ADOX], Visual Basic example
ms.assetid: 7df1089e-69b7-476e-9244-19947c087351
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a38b389c04a6f9c4842c700aac0d87e14299ed31
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286618"
---
# <a name="parameters-collection-command-property-example-vb"></a>Collection de paramètres, exemple de commande de propriété (VB)
Le code suivant montre comment utiliser le [commande](../../../ado/reference/adox-api/command-property-adox.md) propriété avec le [commande](../../../ado/reference/ado-api/command-object-ado.md) objet à récupérer les informations de paramètre pour la procédure.  
  
```  
' BeginParametersVB  
Sub Main()  
    On Error GoTo ProcedureParametersError  
  
    Dim cnn As New ADODB.Connection  
    Dim cmd As ADODB.Command  
    Dim prm As ADODB.Parameter  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Connection  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Open the catalog  
    Set cat.ActiveConnection = cnn  
  
    ' Get the command object  
    Set cmd = cat.Procedures("CustomerById").Command  
  
    ' Retrieve Parameter information  
    cmd.Parameters.Refresh  
    For Each prm In cmd.Parameters  
        Debug.Print prm.Name & ":" & prm.Type  
    Next  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cmd = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
ProcedureParametersError:  
  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndParametersVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Objet catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Commande, propriété (ADOX)](../../../ado/reference/adox-api/command-property-adox.md)   
 [Objet Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
