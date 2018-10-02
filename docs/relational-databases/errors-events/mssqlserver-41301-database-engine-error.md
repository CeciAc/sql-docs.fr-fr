---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd700923bb41475c7ee9880f812adf6155407218
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798117"
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41301|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|COMMIT_DEPENDENCY_FAILURE|  
|Texte du message|Une transaction précédente à la transaction actuelle a pris une dépendance ou a été abandonnée, et la transaction en cours ne peut plus être validée.|  
  
## <a name="explanation"></a>Explication  
La transaction a rencontré une erreur de dépendance, et est maintenant vouée à l'échec.  
  
Cette erreur peut également être causée par un nombre de transactions dépendantes trop important. Les transactions d'écriture ne peuvent avoir qu'un nombre limité de transactions dépendantes. Par exemple, cette erreur peut se produire si trop de transactions de lecture essaient de prendre une dépendance sur la transaction de mise à jour.  
  
## <a name="user-action"></a>Action de l'utilisateur  
N'effectuez aucune tâche dans la transaction. Appelez ROLLBACK TRAN pour restaurer la transaction. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a> Voir aussi  
[Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
