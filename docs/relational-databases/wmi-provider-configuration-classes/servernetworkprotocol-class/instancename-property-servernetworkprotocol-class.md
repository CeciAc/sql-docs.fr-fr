---
title: InstanceName, propriété (classe ServerNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- InstanceName Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- InstanceName property
ms.assetid: 456911c1-9881-4574-8576-0070eff78c27
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4e58bfcdcb0648c176c00234d1e7f7802ebe8500
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51214723"
---
# <a name="instancename-property-servernetworkprotocol-class"></a>Propriété InstanceName (classe ServerNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient le nom de l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui est référencé par le protocole réseau serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.InstanceName [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe ServerNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) qui représente le protocole réseau utilisé par l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur de chaîne qui spécifie le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] référencée par le protocole réseau serveur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
