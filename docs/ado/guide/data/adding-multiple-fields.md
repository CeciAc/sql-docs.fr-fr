---
title: Ajout de plusieurs champs | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 90904154f324a86088fac0d637301193464feb2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701235"
---
# <a name="adding-multiple-fields-and-values"></a>Ajout de plusieurs champs et valeurs
Parfois, il peut être plus efficace de passer un tableau de champs et leurs valeurs correspondantes pour le **AddNew** (méthode), plutôt que de paramètre **valeur** plusieurs fois pour chaque nouveau champ. Si *FieldList* est un tableau, *valeurs* doit également être un tableau avec le même nombre de membres ; sinon, une erreur se produit. L’ordre des noms de champ doit correspondre à l’ordre des valeurs de champ dans chaque tableau. Le code suivant passe un tableau de champs et un tableau de valeurs à la **AddNew** (méthode).

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```
