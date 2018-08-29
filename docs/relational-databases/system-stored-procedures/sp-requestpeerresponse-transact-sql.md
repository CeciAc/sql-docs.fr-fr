---
title: sp_requestpeerresponse (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords:
- sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b722bac6727e6d64bb0c2c475ca900ea78c8fc1d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024371"
---
# <a name="sprequestpeerresponse-transact-sql"></a>sp_requestpeerresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Lorsque cette procédure est exécutée depuis un nœud dans une topologie d'égal à égal, elle demande une réponse de tous les nœuds de la topologie. En exécutant cette procédure et en vérifiant les réponses correspondantes, vous garantissez la remise de toutes les commandes précédentes aux nœuds qui répondent. Cette procédure stockée est exécutée sur le nœud demandeur sur n'importe quelle base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_requestpeerresponse [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
    [ , [ @request_id = ] request_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication**=] **'***publication***'**  
 Nom de la publication dans une topologie d'égal à égal dont l'état est vérifié. *publication* est **sysname**, sans valeur par défaut.  
  
 [ **@description**=] **'***description***'**  
 Informations définies par l'utilisateur utilisables pour identifier des demandes d'état individuelles. *Description* est **nvarchar (4000)**, avec NULL comme valeur par défaut.  
  
 [ **@request_id** =] *request_id*  
 Renvoie l'ID de la nouvelle demande. *request_id* est **int** et est un paramètre de sortie. Cette valeur peut être utilisée lors de l’exécution [sp_helppeerresponses &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) pour afficher toutes les réponses à une demande d’état.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_requestpeerresponse** est utilisé dans la réplication transactionnelle peer-to-peer.  
  
 **sp_requestpeerresponse** permet de s’assurer que toutes les commandes ont été reçus par tous les autres nœuds avant la restauration d’une base de données publiée dans une topologie d’égal à égal. Cette procédure est également utilisée lors de la réplication de modifications DDL (Data Definition Language) effectuées lorsqu'un nœud était hors ligne, pour déterminer le moment où les modifications arrivent sur les autres nœuds.  
  
 **sp_requestpeerresponse** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_requestpeerresponse**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
