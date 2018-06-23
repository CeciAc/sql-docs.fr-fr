---
title: Méthodes de planification | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10513c14e2d9c65a210eee837ce3c23b21ff77aa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039002"
---
# <a name="scheduling-methods"></a>Méthodes de planification
  Vous pouvez utiliser ces méthodes pour créer et gérer des planifications partagées pour l'exécution et la remise de rapports, et pour mettre en cache des plans d'actualisation utilisés par le serveur de rapports.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|Crée un plan d'actualisation du cache pour un élément.|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|Crée une planification partagée.|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|Supprime un plan d'actualisation du cache.|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|Supprime une planification partagée en fonction de son ID.|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|Retourne les propriétés du plan d'actualisation du cache spécifié.|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|Retourne les valeurs des propriétés d'une planification partagée.|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|Retourne une liste des plans d'actualisation du cache associés à un élément de catalogue.|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|Retourne une liste des éléments associés à une planification partagée.|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|Retourne une liste de toutes les planifications partagées du serveur de rapports ou du site SharePoint.|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|Retourne une liste d'états de planification pris en charge.|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|Suspend l'exécution d'une planification donnée.|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|Reprend une planification partagée qui a été suspendue.|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|Définit les propriétés d'un plan d'actualisation du cache.|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|Définit la valeur des propriétés d'une planification partagée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../report-server-web-service.md)   
 [Méthodes du service web Report Server](report-server-web-service-methods.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  