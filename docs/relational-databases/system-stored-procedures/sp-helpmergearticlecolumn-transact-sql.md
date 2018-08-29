---
title: sp_helpmergearticlecolumn (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergearticlecolumn
- sp_helpmergearticlecolumn_TSQL
helpviewer_keywords:
- sp_helpmergearticlecolumn
ms.assetid: 651c017b-9e9a-48f2-a0bd-6fc896eab334
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 82240c6d24f6387e8d1a9e6e105e8fdc9e0ee9e2
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025238"
---
# <a name="sphelpmergearticlecolumn-transact-sql"></a>sp_helpmergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie la liste des colonnes de l'article de table ou de vue spécifié pour une réplication de fusion. Étant donné que les procédures stockées n'ont pas de colonnes, cette procédure stockée renvoie une erreur si une procédure stockée est spécifiée en tant qu'article. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergearticlecolumn [ @publication = ] 'publication' ]  
        , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@article=**] **'***article***'**  
 Est le nom d’une table ou une vue qui est l’article pour récupérer des informations sur. *article* est **sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**sysname**|Identifie la colonne.|  
|**column_name**|**sysname**|Nom de la colonne d'une table ou d'une vue.|  
|**Publié**|**bit**|Indique si le nom de la colonne est publié.<br /><br /> **1** Spécifie que la colonne est publiée.<br /><br /> **0** Spécifie qu’elle n’est pas publiée.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergearticlecolumn** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **replmonitor** du rôle fixe de base de données dans la base de données de distribution ou de la liste d’accès à la publication peuvent exécuter **sp_helpmergearticlecolumn**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
