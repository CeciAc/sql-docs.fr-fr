---
title: Se connecter au serveur (Oracle), Connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f3f1b07feed76a99c1d878cc9c93a6cc65603fe4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248462"
---
# <a name="connect-to-server-oracle-login"></a>Se connecter au serveur (Oracle), Connexion
  Utilisez l'onglet **Connexion** de la boîte de dialogue **Se connecter au serveur** pour définir le compte sous lequel les connexions sont effectuées du serveur de distribution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers le serveur de publication Oracle. Vous devez utiliser le compte défini pour le schéma utilisateur d'administration de réplication au cours de la configuration du serveur de publication. Pour plus d’informations, consultez [Configurer un serveur de publication Oracle](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Options  
 **Instance de serveur**  
 Nom TNS (Transparent Network Substrate) du serveur de publication Oracle, défini au cours de la configuration du logiciel client Oracle installé sur le serveur de distribution.  
  
 **Authentification**  
 Sélectionnez **Authentification standard Oracle** (recommandé) ou **Authentification Windows**. Si vous sélectionnez **Authentification Windows**:  
  
-   Le serveur Oracle doit être configuré pour permettre les connexions en utilisant les informations d'identification Windows. Pour plus d'informations, consultez votre documentation Oracle.  
  
-   Vous devez être connecté avec le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows que vous avez défini pour le schéma utilisateur d'administration de réplication.  
  
 **Connexion** et **Mot de passe**  
 Si vous avez sélectionné **Authentification standard Oracle** pour l'option d' **authentification** , définissez la connexion et le mot de passe à utiliser qui doivent être identiques à ceux du schéma utilisateur d'administration de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
