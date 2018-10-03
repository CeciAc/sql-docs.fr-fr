---
title: DefinedSize, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4267776593637a01aef38a218f7272261fd1d448
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789187"
---
# <a name="definedsize-property"></a>DefinedSize, propriété
Indique la capacité de données d’un [champ](../../../ado/reference/ado-api/field-object.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Long** valeur qui reflète la taille définie pour un champ, qui varie selon le type de données de l’objet de champ ; consultez [Type](../../../ado/reference/ado-api/type-property-ado.md) pour plus d’informations. Pour un champ qui utilise un type de données de longueur fixe, la valeur de retour est la taille du type de données en octets. Pour un champ qui utilise un type de données de longueur variable, c’est une des opérations suivantes :  
  
1.  La longueur maximale du champ en caractères (pour **adVarChar** et **adVarWChar**) ou en octets (pour **adVarBinary**, et **adVarNumeric**) si le champ a une longueur définie. Par exemple, **adVarChar(5)** champ a une longueur maximale de 5.  
  
2.  La longueur maximale du type de données en caractères (pour **adChar** et **adWChar**) ou en octets (pour **adBinary** et **adNumeric**) si le champ n’est pas une durée définie.  
  
3.  ~ 0 (au niveau du bit, la valeur n’est pas 0 ; tous les bits sont définis sur 1) si aucun des champs et le type de données a une longueur maximale définie.  
  
4.  Pour les types de données qui n’ont pas une longueur, il est défini sur ~ 0 (au niveau du bit, la valeur n’est pas 0 ; tous les bits sont définis sur 1).  
  
## <a name="remarks"></a>Notes  
 Utilisez le **DefinedSize** propriété afin de déterminer la capacité de données d’un **champ** objet.  
  
 Le **DefinedSize** et [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) propriétés sont différentes. Par exemple, considérez un **champ** objet avec un type déclaré de **adVarChar** et un **DefinedSize** valeur de propriété de 50, contenant un seul caractère. Le **ActualSize** valeur de propriété retournée est la longueur en octets du caractère unique.  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActualSize et DefinedSize, exemple de propriétés (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize et DefinedSize, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [ActualSize, propriété (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
