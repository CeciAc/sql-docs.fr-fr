---
title: L’inscription d’objets métier sur le Client pour une utilisation avec DCOM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 31af4a68ec830a5fd514173c831ce3863fef7443
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922355"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Inscription d’objets métier sur le client en vue d’une utilisation avec DCOM
Objets métier personnalisés doivent faire en sorte que du côté client peut mapper son nom de programme (ProgId) à un identificateur (CLSID) qui peut être utilisé via DCOM. Pour cette raison, le ProgID de l’objet DCOM doit être dans le Registre côté client et mappez à l’ID de classe de l’objet métier côté serveur. Pour les autres protocoles pris en charge (HTTP, HTTPS et processus), cela n’est pas nécessaire.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Par exemple, si vous exposez un objet métier côté serveur appelé MyBObj associé à un ID de classe spécifique, par exemple, « {00112233-4455-6677-8899-00AABBCCDDEE} », assurez-vous que les entrées suivantes sont ajoutées au Registre côté client :  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


