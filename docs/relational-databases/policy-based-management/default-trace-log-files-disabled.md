---
title: Fichiers journaux des traces par défaut désactivés
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a816912147038cd49b35ba29bfec732410c2ca91
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616039"
---
# <a name="default-trace-log-files-disabled"></a>Fichiers journaux des traces par défaut désactivés
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie la valeur de l'option default trace enabled (trace par défaut activée) de la procédure stockée sp_configure pour déterminer si la trace par défaut est définie sur ON (1) ou sur OFF (0). Lorsque cette option est activée, le traçage par défaut fournit des informations sur les modifications DDL et de configuration du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Ces informations peuvent être utiles aux clients, mais aussi au service clientèle et au support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)] quand il s’agit de résoudre des problèmes liés à [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez la procédure stockée sp_configure pour activer le traçage en définissant la valeur de l'option default trace enabled sur 1.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Options de configuration de serveur &#40;SQLServer&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
