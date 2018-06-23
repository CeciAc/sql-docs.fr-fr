---
title: Classement et les Types de données d’intégration CLR | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7c7d9f8cfe55a12237e2a2bf30b35ed1a57c5ec2
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694340"
---
# <a name="collation-and-clr-integration-data-types"></a>Classement et types de données de l'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], le **CompareInfo** objet gère les classements. Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] application d’utilisent des interfaces de programmation (API) de la chaîne du **CompareInfo** propriété associée à la **CultureInfo** objet du thread actuel pour effectuer des comparaisons de chaînes. Le paramètre par défaut de la **CultureInfo** objet est basé sur le [!INCLUDE[msCoName](../../includes/msconame-md.md)] paramètres régionaux Windows pour l’ordinateur sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Ce paramètre détermine la sémantique de comparaison par défaut, si aucun explicite **CultureInfo** est spécifié, pour les comparaisons de **System.String** valeurs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne change pas explicitement le **CompareInfo** propriété de classement de la base de données ou serveur. Si nécessaire, les utilisateurs doivent définir approprié **CompareInfo** propriété dans leurs routines.  
  
## <a name="parameter-collation"></a>Paramètre Collation  
 Lorsque vous créez une routine du common language runtime (CLR), et un paramètre d’une méthode CLR liée à la routine est de type **SQLString**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une instance du paramètre avec le classement par défaut de la base de données qui contient la routine d’appel. Si un paramètre n’est pas un **SqlType** (par exemple, **chaîne** plutôt que **SQLString**), les informations de classement de la base de données ne sont pas associées avec le paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
