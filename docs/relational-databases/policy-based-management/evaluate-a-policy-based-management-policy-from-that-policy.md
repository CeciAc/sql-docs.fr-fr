---
title: Évaluer une stratégie de gestion basée sur des stratégies à partir de cette stratégie | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5ce3203f17a32f0fb0615151be30ec740c93165d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137812"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a>Évaluer une stratégie de gestion basée sur des stratégies pour cette stratégie
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment évaluer une stratégie à l'aide de cette stratégie dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour évaluer une stratégie à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy"></a>Pour évaluer une stratégie  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient la stratégie que vous souhaitez évaluer.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Stratégies** .  
  
5.  Cliquez avec le bouton droit sur la stratégie à évaluer, puis sélectionnez **Évaluer**.  
  
6.  La boîte de dialogue **Résultats d'évaluation**  indique les résultats de l'évaluation de la stratégie. Pour les cibles qui ne sont pas conformes à la stratégie et ont des propriétés qui peuvent être reconfigurées par la Gestion basée sur des stratégies, vous pouvez imposer la conformité en cliquant sur **Appliquer**. Pour plus d'informations sur les options disponibles de la boîte de dialogue **Évaluer les stratégies** , consultez [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md) et [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md).  
  
7.  Lorsque vous avez terminé, cliquez sur **Fermer**.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

