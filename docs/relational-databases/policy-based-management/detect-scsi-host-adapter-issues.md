---
title: Détecter des problèmes de carte hôte SCSI | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 75225b64-c102-4f1b-888a-fe72710dbfcd
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d26498c6006c867bd2123e3bb8a37112773ac450
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007620"
---
# <a name="detect-scsi-host-adapter-issues"></a>Détecter des problèmes de carte hôte SCSI
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle recherche l’ID d’événement 1066 dans le journal des événements système. Cette erreur est due à des problèmes de configuration de l'adaptateur hôte SCSI ou au mauvais fonctionnement d'un périphérique.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Pour plus d'informations sur la résolution de cette erreur, consultez l'article suivant de la Base de connaissances Microsoft :  
  
-   [Article 311081 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117744)  
  
  
