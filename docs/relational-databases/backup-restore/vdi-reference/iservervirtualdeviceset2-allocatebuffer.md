---
title: IServerVirtualDeviceSet2::AllocateBuffer
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::AllocateBuffer.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8c28009fae8b52264b541ca3eb4281ab9abccf63
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847490"
---
# <a name="iservervirtualdeviceset2allocatebuffer-vdi"></a>IServerVirtualDeviceSet2::AllocateBuffer (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **AllocateBuffer** obtient une mémoire tampon partagée de l’ensemble d’appareils virtuels.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDeviceSet2::AllocateBuffer (
   LPVOID*      ppBuffer,
   UINT32      dwSize,
   UINT32      dwAlignment
);
```

## <a name="parameters"></a>Paramètres

*ppBuffer* : retourne un pointeur vers le début de la mémoire tampon.

*dwSize* : la taille de la mémoire tampon en octets. Ceci n’inclut pas les zones de préfixe demandées par le client. Ces zones sont masquées sur le serveur et il existe un espace disponible avant que l’adresse de la mémoire tampon ne soit retournée.

*dwAlignment* : spécifie la limite d’alignement pour la mémoire tampon. Par exemple, la valeur 4 096 garantit que la mémoire tampon est alignée sur une limite de 4 096 octets. Cela signifie que l’adresse retournée aurait les 12 bits de poids faible définis sur zéro. Ce paramètre doit être une puissance de 2.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La mémoire tampon est retournée. |
| VD_E_MEMORY | Une condition de mémoire insuffisante s’est produite. |
| VD_E_INVALID | Un paramètre était non valide. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).