---
title: Présentation de la gestion des exceptions dans Reporting Services | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ee084e9d85a1bee21db3994be8b9473daefc7c0f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62992236"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Présentation de la gestion des exceptions dans Reporting Services
  Si votre application [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] envoie un demande au service Web Report Server, mais que ce dernier ne parvient pas à la traiter, le service retourne une exception SOAP au client. La gestion des exceptions levées par le service Web Report Server est une composante importante des applications que vous développez car vous avez la possibilité de retourner des informations utiles aux utilisateurs lorsque des erreurs se produisent.  
  
 Cette section contient des informations sur la gestion des exceptions, la manière d'éviter les entrées utilisateur non valides et l'envoi d'informations pertinentes sur les erreurs aux utilisateurs. Pour obtenir des informations générales sur la gestion des exceptions, consultez « Gestion et levée des exceptions » dans la documentation du SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Gestion des exceptions dans Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/handling-exceptions-in-reporting-services.md)|Fournit une vue d'ensemble des exceptions dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et le rôle de SOAP dans le renvoi d'erreurs depuis un service Web.|  
|[Meilleures pratiques pour la gestion des exceptions dans Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/best-practices-for-reporting-services-exception-handling.md)|Fournit des recommandations sur la manière de gérer les exceptions dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[Classe SoapException Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)|Décrit la classe **SoapException** dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications à l’aide du service web et de .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
