---
title: Les Classes fondamentales AMO | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [AMO]
- AMO, database objects
- AMO, server objects
- Analysis Management Objects, server objects
- database objects [AMO]
- Analysis Management Objects, database objects
- AMO, data sources
- Analysis Management Objects, data sources
ms.assetid: 440e9287-53a2-4db3-9481-1d2ceb6e5b5a
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ee31478a526dad385d9721256beebc4324cadb60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142923"
---
# <a name="amo-fundamental-classes"></a>Classes fondamentales AMO
  Les classes fondamentales constituent le point de départ pour utiliser AMO (Analysis Management Objects). À travers ces classes, vous établissez votre environnement pour tous les objets voués à être utilisés dans votre application. Les classes fondamentales se composent des objets suivants : <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource> et <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
 L'illustration suivante montre la relation qui existe entre les classes décrites dans cette rubrique.  
  
 ![Les Classes fondamentales AMO](../../../analysis-services/dev-guide/media/amo-fundamentalclasses.gif "des Classes fondamentales AMO")  
  
  
  
##  <a name="ServerObjects"></a> Objets serveur  
 En outre, vous aurez accès aux méthodes suivantes :  
  
-   gestion des connexions : Connect, Disconnect, Reconnect et GetConnectionState ;  
  
-   gestion des transactions : BeginTransaction, CommitTransaction et RollbackTransaction ;  
  
-   Backup et Restore ;  
  
-   exécution de DDL : Execute, CancelCommand, SendXmlaRequest, StartXmlaRequest ;  
  
-   gestion des métadonnées : UpdateObjects et Validate.  
  
 Pour se connecter à un serveur, vous avez besoin d'une chaîne de connexion standard, comme dans ADOMD.NET et OLEDB. Pour plus d’informations, consultez <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>. Le nom du serveur peut être spécifié sous forme de chaîne de connexion sans qu'il soit nécessaire d'utiliser un format de chaîne de connexion.  
  
 Pour plus d'informations sur les méthodes et les propriétés disponibles, consultez <xref:Microsoft.AnalysisServices.Server> dans <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DatabaseObjects"></a> Objets de base de données  
 Pour utiliser un objet <xref:Microsoft.AnalysisServices.Database> dans votre application, vous devez obtenir une instance de la base de données auprès de la collection de bases de données du serveur parent. Pour créer une base de données, vous devez ajouter un objet <xref:Microsoft.AnalysisServices.Database> à une collection de bases de données du serveur et mettre à jour la nouvelle instance sur le serveur. Pour supprimer une base de données, vous devez supprimer l'objet <xref:Microsoft.AnalysisServices.Database> par le biais de sa propre méthode Drop.  
  
 Les bases de données peuvent être sauvegardées à l'aide de la méthode BackUp (de l'objet <xref:Microsoft.AnalysisServices.Database> ou de l'objet <xref:Microsoft.AnalysisServices.Server>), mais elles ne peuvent être restaurées qu'à partir de l'objet <xref:Microsoft.AnalysisServices.Server> avec la méthode Restore.  
  
 Pour plus d'informations sur les méthodes et les propriétés disponibles, consultez <xref:Microsoft.AnalysisServices.Database> dans <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DSandDSV"></a>Objets DataSource et DataSourceView  
 Les sources de données sont gérées à l'aide de l'objet <xref:Microsoft.AnalysisServices.DataSourceCollection> de la classe Database. Il est possible de créer une instance de <xref:Microsoft.AnalysisServices.DataSource> en utilisant la méthode Add d'un objet <xref:Microsoft.AnalysisServices.DataSourceCollection>. Une instance de <xref:Microsoft.AnalysisServices.DataSource> peut être supprimée en utilisant la méthode Remove d'un objet <xref:Microsoft.AnalysisServices.DataSourceCollection>.  
  
 Les objets <xref:Microsoft.AnalysisServices.DataSourceView> sont gérés à partir de l'objet <xref:Microsoft.AnalysisServices.DataSourceViewCollection> de la classe Database.  
  
 Pour plus d'informations sur les méthodes et les propriétés disponibles, consultez  <xref:Microsoft.AnalysisServices.DataSource> et <xref:Microsoft.AnalysisServices.DataSourceView> dans <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices>   
 [Présentation des Classes AMO](amo-classes-introduction.md)   
 [Programmation des objets principaux AMO](programming-amo-fundamental-objects.md)  
  
  