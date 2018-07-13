---
title: Élément AssociationSet (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 93e5ac4d-d7e8-490e-b775-28263a48cfcc
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d418e75aa451c14db6010f6cb3673cd8c3a74bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229559"
---
# <a name="associationset-element-csdlbi"></a>Élément AssociationSet (CSDLBI)
  L'élément `AssociationSet` est un type complexe qui définit une association. Dans un modèle de données CSDLBI, une association est une relation entre deux tables.  
  
 Un `AssociationSet` doit être spécifié pour chaque relation unique dans un modèle. L'élément `AssociationSet` définit les points de terminaison à l'aide de l'élément `Association`. L'élément `AssociationSet` définit également les métadonnées sur la relation et son utilisation dans le modèle de données.  
  
## <a name="applicable-attributes"></a>Attributs applicables  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément `AssociationSet`.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|État|Oui|Chaîne qui indique si l'association est active ou non. La valeur est définie par l'élément State.|  
|Hidden|non|Valeur booléenne qui indique si la relation est visible. Par défaut, la valeur affectée à Hidden est `false`, ce qui signifie que toutes les relations sont visibles dans le modèle.|  
  
## <a name="state-element"></a>Élément State  
 L'élément `State` est un type simple qui indique si une association est active, et doit être utilisée dans les calculs, ou inactive et doit être référencée explicitement dans les calculs.  
  
 Si plusieurs ensembles d'associations connectent deux entités, un seul ensemble d'associations peut être signalé comme étant actif. En d'autres termes, s'il existe deux relations entre les deux mêmes tables, une seule relation peut être active.  
  
 Le tableau suivant répertorie les valeurs de l'élément `State`.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Actif|L'association est active.|  
|Inactif|L'association est active.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant illustre une relation dans le modèle tabulaire AdventureWorks (en CSDLBI version 1.1). La relation est marquée comme étant Inactive, car il existe une relation (entre OrderKey et Date).  
  
```  
<AssociationSet   
    Name="InternetSales_Date_Date_Date"  
    Association="Sandbox.InternetSales_Date_Date_Date">  
    <End EntitySet="InternetSales" />  
    <End EntitySet="DimDate" />  
<bi:AssociationSet State="Inactive" />  
</AssociationSet>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple ci-dessous illustre une relation définie entre les tables Sales et Currency, dans le cube Contoso Operations.  
  
```  
<AssociationSet   
    Name ="Sales_Currency_Currency_Currency_Name2"  
    Association ="Sandbox.Sales_Currency_Currency_Currency_Name2">  
    <End EntitySet ="Sales" />  
    <End EntitySet ="Currency" />  
<bi:AssociationSet />  
</AssociationSet>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
