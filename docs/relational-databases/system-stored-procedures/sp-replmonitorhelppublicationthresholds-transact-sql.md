---
title: sp_replmonitorhelppublicationthresholds (T-SQL)
description: Décrit la procédure stockée sp_replmonitorhelppublicationthresholds qui retourne les métriques de seuil définies pour une publication analysée.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
author: stevestein
ms.author: sstein
ms.openlocfilehash: d351db8ca696263f294f5a52f364d42ac48bad24
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75320776"
---
# <a name="sp_replmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne l'ensemble de mesures de seuil pour une publication analysée. Cette procédure stockée, utilisée pour surveiller la réplication, est exécutée sur la base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replmonitorhelppublicationthresholds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données publiée. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication_type = ] publication_type`Si le type de publication. *publication_type* est de **type int**et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Publication transactionnelle.|  
|**1,0**|Publication d'instantané.|  
|**2**|Publication de fusion.|  
|NULL (par défaut)|La réplication tente de déterminer le type de publication.|  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**tiers**|ID de la mesure de performance de réplication qui peut correspondre à l'une des valeurs suivantes.<br /><br /> **1expiration** : contrôle l’expiration imminente des abonnements aux publications transactionnelles.<br /><br /> **2latency** : analyse les performances des abonnements aux publications transactionnelles.<br /><br /> **4mergeexpiration** : contrôle l’expiration imminente des abonnements aux publications de fusion.<br /><br /> **5mergeslowrunduration** : contrôle la durée des synchronisations de fusion sur les connexions à faible bande passante (accès à distance).<br /><br /> **6mergefastrunduration** : contrôle la durée des synchronisations de fusion sur les connexions à bande passante élevée (LAN).<br /><br /> **7mergefastrunspeed** : contrôle la vitesse de synchronisation des synchronisations de fusion sur les connexions à bande passante élevée (LAN).<br /><br /> **8mergeslowrunspeed** : contrôle la vitesse de synchronisation des synchronisations de fusion sur les connexions à faible bande passante (accès à distance).|  
|**bonhomme**|**sysname**|Nom de la mesure de performance de réplication.|  
|**ajoutée**|**tiers**|Valeur seuil de la mesure de performance.|  
|**shouldalert**|**64bits**|Indique si une alerte doit être générée lorsque la mesure dépasse le seuil défini pour cette publication ; la valeur **1** indique qu’une alerte doit être déclenchée.|  
|**IsEnabled**|**64bits**|Indique si l’analyse est activée pour cette mesure de performance de réplication pour cette publication ; la valeur **1** indique que l’analyse est activée.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_replmonitorhelppublicationthresholds** est utilisé avec tous les types de réplications.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle de base de données fixe **db_owner** ou **replmonitor** sur la base de données de distribution peuvent exécuter **sp_replmonitorhelppublicationthresholds**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
