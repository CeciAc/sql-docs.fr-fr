---
title: Transformations XSLT | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2606733b3efc5a9641f8de0f544b3cff7c7e9a31
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923341"
---
# <a name="xslt-transformations"></a>Transformations XSLT
XSLT peut être appliqué pour le code XML généré pour le transformer en un autre format. Comprendre le format XML dans ADO permet de développer des modèles XSLT qui peuvent transformer en un format plus convivial.  
  
 Par exemple, vous savez que chaque ligne de l’objet Recordset est enregistré en tant qu’élément z : row dans l’élément rs : data. De même, chaque champ de l’objet Recordset est enregistré comme une paire attribut-valeur pour cet élément.  
  
## <a name="remarks"></a>Notes  
 Le script XSLT suivant peut être appliqué au document XML indiqué dans la section précédente pour le transformer en un tableau HTML à afficher dans le navigateur :  
  
```  
<?xml version="1.0" encoding="ISO-8859-1"?>  
<html xmlns:xsl="http://www.w3.org/TR/WD-xsl">  
<body STYLE="font-family:Arial, helvetica, sans-serif; font-size:12pt; background-color:white">  
<table border="1" style="table-layout:fixed" width="600">  
  <col width="200"></col>  
  <tr bgcolor="teal">  
    <th><font color="white">CustomerId</font></th>  
    <th><font color="white">CompanyName</font></th>  
    <th><font color="white">ContactName</font></th>  
  </tr>  
<xsl:for-each select="xml/rs:data/z:row">  
  <tr bgcolor="navy">  
    <td><font color="white"><xsl:value-of select="@CustomerID"/></font></td>  
    <td><font color="white"><xsl:value-of select="@CompanyName"/></font></td>  
    <td><font color="white"><xsl:value-of select="@ContactName"/></font></td>   
  </tr>  
</xsl:for-each>  
</table>  
</body>  
</html>  
```  
  
 XSLT convertit le flux XML généré par la méthode Save d’ADO dans une table HTML qui affiche chaque champ de l’ensemble d’enregistrements, ainsi que le titre de la table. Lignes et en-têtes des colonnes sont également affectés différentes polices et couleurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
