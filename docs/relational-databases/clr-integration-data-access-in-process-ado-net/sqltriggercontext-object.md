---
title: SqlTriggerContext, objet | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3b4c34b6412d531444b8f1d38be15fe9d20ea139
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35700240"
---
# <a name="sqltriggercontext-object"></a>Objet SqlTriggerContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La classe **SqlTriggerContext** fournit des informations de contexte sur le déclencheur. Ces informations contextuelles comprennent le type d'action ayant provoqué l'activation du déclencheur, les colonnes qui ont été modifiées dans une opération UPDATE et, dans le cas d'un déclencheur en langage de définition de données (DDL), une structure **EventData** XML qui décrit l'opération de déclenchement. Pour plus d’informations et des exemples montrant comment utiliser les **SqlTriggerContext** de classe, consultez [déclencheurs CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
 Pour plus d'informations, consultez la documentation de référence sur la classe **Microsoft.SqlServer.Server.SqlTriggerContext** dans la documentation du Kit de développement logiciel (SDK) .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
