---
title: 'Erreur du serveur Internet : Accès refusé | Documents Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28e175b244c538fb0bab9d7adfdc1fcf6c2a48bf
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273988"
---
# <a name="internet-server-error-access-denied"></a>Erreur de serveur Internet : Accès refusé
Si vous obtenez cette erreur, cela signifie que Microsoft Internet Information Services (IIS) a retourné l’état suivant :  
  
 HTTP_STATUS_DENIED 401  
  
 Assurez-vous que les répertoires accédés par IIS disposent des autorisations appropriées. Services Bureau à distance peut communiquer avec un serveur Web IIS en cours d’exécution dans l’un des trois modes d’authentification de mot de passe : anonyme, Basic ou stimulation/réponse NT (appelée authentification Windows intégrée dans Windows 2000). En outre, le serveur Web doit avoir des autorisations à l’ordinateur source de données s’il s’agit d’un ordinateur Windows NT et Windows 2000.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




