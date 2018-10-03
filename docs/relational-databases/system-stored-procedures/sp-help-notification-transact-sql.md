---
title: sp_help_notification (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_notification
- sp_help_notification_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_notification
ms.assetid: 0273457f-9d2a-4a6f-9a16-6a6bf281cba0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3ccc926844f6d3c054a69cb51f3156dc8e186a98
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833577"
---
# <a name="sphelpnotification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit une liste d'alertes pour un opérateur donné ou une liste d'opérateurs pour une alerte donnée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_notification  
     [ @object_type = ] 'object_type' ,  
     [ @name = ] 'name' ,  
     [ @enum_type = ] 'enum_type' ,   
     [ @notification_method = ] notification_method   
     [ , [ @target_name = ] 'target_name' ]   
```  
  
## <a name="arguments"></a>Arguments  
 [ **@object_type =**] **'***object_type***'**  
 Type d'informations à retourner. *object_type*est **char (9)**, sans valeur par défaut. *object_type* peuvent être des alertes, qui répertorie les alertes affectées au nom d’opérateur fourni *,* ou OPERATORS, qui répertorie les opérateurs responsables du nom d’alerte fourni *.*  
  
 [  **@name =**] **'***nom***'**  
 Nom d’opérateur (si *object_type* est OPERATORS) ou un nom de l’alerte (si *object_type* est ALERTS). *nom* est **sysname**, sans valeur par défaut.  
  
 [  **@enum_type =**] **'***type_de_liste***'**  
 Le *object_type*informations qui sont retournées. *type_de_liste* prend la valeur ACTUAL dans la plupart des cas. *type_de_liste*est **char (10)**, sans valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|ACTUAL|Répertorie uniquement les *object_types* associés *nom*.|  
|ALL|Répertorie tous les*object_types* y compris ceux qui ne sont pas associés *nom*.|  
|TARGET|Répertorie uniquement les *object_types* correspondant fourni *target_name*, quelle que soit l’association avec*nom*.|  
  
 [  **@notification_method =**] *méthode_de_notification*  
 Valeur numérique qui détermine les colonnes de méthode de notification à retourner. *méthode_de_notification* est **tinyint**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Messagerie électronique : retourne uniquement le **use_email** colonne.|  
|**2**|Radiomessagerie : retourne uniquement le **use_pager** colonne.|  
|**4**|NetSend : retourne uniquement le **use_netsend** colonne.|  
|**7**|Tout : retourne toutes les colonnes.|  
  
 [  **@target_name =**] **'***target_name***'**  
 Nom d’alerte à rechercher (si *object_type* est ALERTS) ou un nom d’opérateur à rechercher (si *object_type* est OPERATORS). *target_name* est nécessaire uniquement si *type_de_liste* est la cible. *target_name* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-valves"></a>Valeur des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Si *object_type* est **alertes**, le jeu de résultats répertorie toutes les alertes pour un opérateur donné.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**Int**|Numéro d'identification de l'alerte.|  
|**alert_name**|**sysname**|Nom de l’alerte.|  
|**use_email**|**Int**|Un message électronique est utilisé pour avertir l'opérateur.<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**use_pager**|**Int**|La radiomessagerie est utilisée pour avertir l'opérateur.<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**use_netsend**|**Int**|Le réseau est utilisé pour avertir l'opérateur :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**has_email**|**Int**|Nombre de notifications envoyées par messagerie électronique pour cette alerte.|  
|**has_pager**|**Int**|Nombre de notifications envoyées par radiomessagerie pour cette alerte.|  
|**has_netsend**|**Int**|Nombre de **net send** notifications envoyées pour cette alerte.|  
  
 Si **object_type** est **opérateurs**, le jeu de résultats répertorie tous les opérateurs pour une alerte donnée.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**operator_id**|**Int**|Numéro d'identification de l'opérateur.|  
|**operator_name**|**sysname**|Nom de l’opérateur.|  
|**use_email**|**Int**|Un message électronique est utilisé pour envoyer la notification à l'opérateur :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**use_pager**|**Int**|La radiomessagerie est utilisée pour envoyer la notification à l'opérateur :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**use_netsend**|**Int**|Le réseau est utilisé pour avertir l’opérateur :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**has_email**|**Int**|L'opérateur possède une adresse électronique :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**has_pager**|**Int**|L'opérateur possède une adresse de radiomessagerie :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**has_netsend**|**Int**|Une notification d'envoi réseau est configurée pour l'opérateur.<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée doit être exécutée à partir de la **msdb** base de données.  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette procédure stockée, l'utilisateur doit être membre du rôle de serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-alerts-for-a-specific-operator"></a>A. Affichage d'une liste d'alertes pour un opérateur spécifique  
 L'exemple suivant retourne toutes les alertes dont l'opérateur `François Ajenstat` est notifié.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_notification   
    @object_type = N'ALERTS',  
    @name = N'François Ajenstat',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
### <a name="b-listing-operators-for-a-specific-alert"></a>B. Affichage d'une liste d'opérateurs pour une alerte spécifique  
 L'exemple suivant retourne tous les opérateurs qui reçoivent une notification quelconque pour l'alerte `Test Alert`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_notification  
    @object_type = N'OPERATORS',  
    @name = N'Test Alert',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
