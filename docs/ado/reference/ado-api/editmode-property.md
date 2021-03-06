---
title: EditMode, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0ffc6fb258799b0ab0bb03e7acbd922f6a67d1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918981"
---
# <a name="editmode-property"></a>EditMode, propriété
Indique l’état de modification de l’enregistrement en cours.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) valeur.  
  
## <a name="remarks"></a>Notes  
 ADO gère une mémoire tampon d’édition associé à l’enregistrement actif. Cette propriété indique si les modifications ont été apportées à cette mémoire tampon, ou si un nouvel enregistrement a été créé. Utilisez le **EditMode** propriété afin de déterminer l’état de modification de l’enregistrement en cours. Vous pouvez tester pour les modifications en attente si un processus de modification a été interrompu et déterminer s’il faut utiliser le [mise à jour](../../../ado/reference/ado-api/update-method.md) ou [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) (méthode).  
  
 Dans *en mode de mise à jour immédiate* le **EditMode** propriété est réinitialisée à **adEditNone** après un appel réussi au **mettre à jour** méthode est appelée. . Lorsqu’un appel à [supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md) ne pas supprimer l’ou les enregistrements dans la source de données (par exemple, en raison de violations d’intégrité référentielle), la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) reste en mode d’édition (**EditMode** = **adEditInProgress**). Par conséquent, **CancelUpdate** doit être appelée avant de déplacer l’enregistrement en cours (par exemple avec [déplacer](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), ou [fermer](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 Dans *mode de mise à jour par lots* (dans lequel le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode), la valeur de la **EditMode**  propriété est modifiée lorsque la première opération est effectuée et il n’est pas réinitialisé par un appel à la **mise à jour** (méthode). Les opérations suivantes ne modifiez pas la valeur de la **EditMode** propriété, même si différentes opérations sont effectuées. Par exemple, si la première opération consiste à ajouter un nouvel enregistrement, et la seconde apporte des modifications à un enregistrement, la propriété de **EditMode** seront toujours **adEditAdd**. Le **EditMode** propriété n’est pas réinitialisée à **adEditNone** jusqu'à ce qu’après l’appel à **UpdateBatch**. Pour déterminer quelles opérations ont été effectuées, définissez le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété [adFilterPending](../../../ado/reference/ado-api/filtergroupenum.md) afin que seuls les enregistrements avec des modifications en attente seront visibles et examiner les [état](../../../ado/reference/ado-api/status-property-ado-recordset.md) propriété de chaque enregistrement pour déterminer quelles modifications ont été apportées aux données.  
  
> [!NOTE]
>  **EditMode** peut retourner une valeur valide uniquement s’il existe un enregistrement en cours. **EditMode** retournera une erreur si [BOF ou EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) a la valeur true, ou si l’enregistrement en cours a été supprimé.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CursorType, LockType et EditMode, exemple de propriétés (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType et EditMode, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [AddNew, méthode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [DELETE, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Update, méthode](../../../ado/reference/ado-api/update-method.md)
