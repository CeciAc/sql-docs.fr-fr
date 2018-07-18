---
title: Append (méthode) (clés ADOX) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eaef312977613409453dfa1d876674d6b95c927
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284818"
---
# <a name="append-method-adox-keys"></a>Append (méthode) (clés ADOX)
Ajoute un nouveau [clé](../../../ado/reference/adox-api/key-object-adox.md) de l’objet à la [clés](../../../ado/reference/adox-api/keys-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Clé*  
 Le **clé** objet à ajouter ou le nom de la clé à créer et à ajouter.  
  
 *KeyType*  
 Facultatif. A **Long** valeur qui spécifie le type de clé. Le *clé* paramètre correspond à la [Type](../../../ado/reference/adox-api/type-property-key-adox.md) propriété d’un **clé** objet.  
  
 *Colonne*  
 Facultatif. A **chaîne** valeur qui spécifie le nom de la colonne à indexer. Le *colonnes* paramètre correspond à la valeur de la [nom](../../../ado/reference/adox-api/name-property-adox.md) propriété d’un [colonne](../../../ado/reference/adox-api/column-object-adox.md) objet.  
  
 *RelatedTable*  
 Facultatif. A **chaîne** valeur qui spécifie le nom de la table associée. Le *RelatedTable* paramètre correspond à la valeur de la **nom** propriété d’un [Table](../../../ado/reference/adox-api/table-object-adox.md) objet.  
  
 *RelatedColumn*  
 Facultatif. A **chaîne** valeur qui spécifie le nom de la colonne liée pour une clé étrangère. Le *RelatedColumn* paramètre correspond à la valeur de la **nom** propriété d’un [colonne](../../../ado/reference/adox-api/column-object-adox.md) objet.  
  
## <a name="remarks"></a>Notes  
 Le *colonnes* paramètre peut prendre le nom d’une colonne ou un tableau de noms de colonnes.  
  
## <a name="applies-to"></a>S'applique à  
 [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule exemple (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append (méthode) (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (méthode) (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (méthode) (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (méthode) (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (méthode) (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (méthode) (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
