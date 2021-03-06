---
title: Configurer le Gestionnaire de rapports pour passer des Cookies d’authentification personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34f637ee2d0a8235f21167df78178c4de9292c8c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66102047"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>Configurer le Gestionnaire de rapports pour passer des cookies d'authentification personnalisée
  Si vous utilisez une extension d'authentification personnalisée, vous devez configurer le Gestionnaire de rapports pour transmettre des cookies d'authentification personnalisée. Sinon, le Gestionnaire de rapports transmet uniquement des cookies via des demandes HTTP spécifiques au serveur de rapports. Si vous souhaitez transmettre des cookies supplémentaires, vous devez modifier le fichier RSReportServer.Config.  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>Modification du fichier RSReportServer.Config  
 Vous pouvez activer le Gestionnaire de rapports pour transmettre des cookies supplémentaires via le serveur de rapports en ajoutant une <`PassThroughCookies`> élément pour les paramètres de configuration du Gestionnaire de rapports dans le fichier RSReportServer.config. La transmission de cookies supplémentaires est utile dans une solution d'authentification unique qui requiert non seulement les cookies d'authentification du serveur de rapports mais également les cookies d'un système d'authentification tiers.  
  
 Pour activer la transmission de cookies supplémentaires via des requêtes HTTP lorsque vous utilisez le Gestionnaire de rapports, définissez les éléments ci-après dans le fichier RSReportServer.config :  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification avec le serveur de rapports](authentication-with-the-report-server.md)   
 [Fichier de Configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Présentation des extensions de sécurité](../extensions/security-extension/security-extensions-overview.md)   
 [Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
