---
title: Colonnes de données d’événements de découverte | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Discover Events event category
ms.assetid: 10ec598e-5b51-4767-b4f7-42e261d96a40
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dae80d01a62d7462287c1a3251da4f780079296a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142139"
---
# <a name="discover-events-data-columns"></a>Colonnes de données des événements de découverte
  La catégorie Événements de découverte contient les classes d'événements suivantes :  
  
-   Classe Discover Begin  
  
-   Classe Discover End  
  
 Les tableaux suivants répertorient les colonnes de données de chacune de ces classes d'événements.  
  
## <a name="discover-begin-classdata-columns"></a>Classe Discover Begin—Colonnes de données  
  
|||||  
|-|-|-|-|  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|EventClass|0| 1|Classe d'événements utilisée pour catégoriser les événements.|  
|EventSubclass| 1| 1|La sous-classe d'événements fournit des informations supplémentaires sur chaque classe d'événements. Les éléments suivants sont une valeur valide : paires de nom :<br /><br /> 0 : **DBSCHEMA_CATALOGS**<br />1 : **DBSCHEMA_TABLES**<br />2 : **DBSCHEMA_COLUMNS**<br />3 : **DBSCHEMA_PROVIDER_TYPES**<br />4 : **MDSCHEMA_CUBES**<br />5 : **MDSCHEMA_DIMENSIONS**<br />6 : **MDSCHEMA_HIERARCHIES**<br />7 : **MDSCHEMA_LEVELS**<br />8 : **MDSCHEMA_MEASURES**<br />9 : **MDSCHEMA_PROPERTIES**<br />10 : **MDSCHEMA_MEMBERS**<br />11 : **MDSCHEMA_FUNCTIONS**<br />12 : **MDSCHEMA_ACTIONS**<br />13 : **MDSCHEMA_SETS**<br />14 : **DISCOVER_INSTANCES**<br />15 : **MDSCHEMA_KPIS**<br />16 : **MDSCHEMA_MEASUREGROUPS**<br />17 : **MDSCHEMA_COMMANDS**<br />18 : **DMSCHEMA_MINING_SERVICES**<br />19 : **DMSCHEMA_MINING_SERVICE_PARAMETERS**<br />20 : **DMSCHEMA_MINING_FUNCTIONS**<br />21 : **DMSCHEMA_MINING_MODEL_CONTENT**<br />22 : **DMSCHEMA_MINING_MODEL_XML**<br />23 : **DMSCHEMA_MINING_MODELS**<br />24 : **DMSCHEMA_MINING_COLUMNS**<br />25 : **DISCOVER_DATASOURCES**<br />26 : **DISCOVER_PROPERTIES**<br />27 : **DISCOVER_SCHEMA_ROWSETS**<br />28 : **DISCOVER_ENUMERATORS**<br />29 : **DISCOVER_KEYWORDS**<br />30 : **DISCOVER_LITERALS**<br />31 : **DISCOVER_XML_METADATA**<br />32 : **DISCOVER_TRACES**<br />33 : **DISCOVER_TRACE_DEFINITION_PROVIDERINFO**<br />34 : **DISCOVER_TRACE_COLUMNS**<br />35 : **DISCOVER_TRACE_EVENT_CATEGORIES**<br />36 : **DMSCHEMA_MINING_STRUCTURES**<br />37 : **DMSCHEMA_MINING_STRUCTURE_COLUMNS**<br />38 : **DISCOVER_MASTER_KEY**<br />39 : **MDSCHEMA_INPUT_DATASOURCES**<br />40 : **DISCOVER_LOCATIONS**<br />41 : **DISCOVER_PARTITION_DIMENSION_STAT**<br />42 : **DISCOVER_PARTITION_STAT**<br />43 : **DISCOVER_DIMENSION_STAT**<br />44 : **MDSCHEMA_MEASUREGROUP_DIMENSIONS**<br />45 : **DISCOVER_XEVENT_TRACE_DEFINITION**|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25| 1|Contient l'ID de connexion unique associé à l'événement de découverte.|  
|DatabaseName|28|8|Nom de la base de données dans laquelle l'instruction de l'utilisateur s'exécute.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement de découverte. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|NTDomainName|33|8|Contient le domaine Windows associé à l'événement de découverte.|  
|ClientProcessID|36| 1|Contient l'ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|Contient l'ID de session associé à l'événement de découverte.|  
|NTCanonicalUserName|40|8|Contient le nom d'utilisateur Windows associé à l'événement de découverte. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|SPID|41| 1|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement de découverte. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|TextData|42|9|Contient les données texte associées à l'événement.|  
|ServerName|43|8|Contient le nom de l'instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l'événement de découverte s'est produit.|  
|RequestProperties|45|9|Contient les propriétés de la demande XMLA (XML for Analysis) associées à l'événement de découverte.|  
  
## <a name="discover-end-classdata-columns"></a>Classe Discover End—Colonnes de données  
  
|||||  
|-|-|-|-|  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|EventClass|0| 1|Contient la classe d'événements ; utilisée pour classer les événements par catégorie.|  
|EventSubclass| 1| 1|La sous-classe d'événements fournit des informations supplémentaires sur chaque classe d'événements. Les éléments suivants sont une valeur valide : paires de nom :<br /><br /> 0 : **DBSCHEMA_CATALOGS**<br />1 : **DBSCHEMA_TABLES**<br />2 : **DBSCHEMA_COLUMNS**<br />3 : **DBSCHEMA_PROVIDER_TYPES**<br />4 : **MDSCHEMA_CUBES**<br />5 : **MDSCHEMA_DIMENSIONS**<br />6 : **MDSCHEMA_HIERARCHIES**<br />7 : **MDSCHEMA_LEVELS**<br />8 : **MDSCHEMA_MEASURES**<br />9 : **MDSCHEMA_PROPERTIES**<br />10 : **MDSCHEMA_MEMBERS**<br />11 : **MDSCHEMA_FUNCTIONS**<br />12 : **MDSCHEMA_ACTIONS**<br />13 : **MDSCHEMA_SETS**<br />14 : **DISCOVER_INSTANCES**<br />15 : **MDSCHEMA_KPIS**<br />16 : **MDSCHEMA_MEASUREGROUPS**<br />17 : **MDSCHEMA_COMMANDS**<br />18 : **DMSCHEMA_MINING_SERVICES**<br />19 : **DMSCHEMA_MINING_SERVICE_PARAMETERS**<br />20 : **DMSCHEMA_MINING_FUNCTIONS**<br />21 : **DMSCHEMA_MINING_MODEL_CONTENT**<br />22 : **DMSCHEMA_MINING_MODEL_XML**<br />23 : **DMSCHEMA_MINING_MODELS**<br />24 : **DMSCHEMA_MINING_COLUMNS**<br />25 : **DISCOVER_DATASOURCES**<br />26 : **DISCOVER_PROPERTIES**<br />27 : **DISCOVER_SCHEMA_ROWSETS**<br />28 : **DISCOVER_ENUMERATORS**<br />29 : **DISCOVER_KEYWORDS**<br />30 : **DISCOVER_LITERALS**<br />31 : **DISCOVER_XML_METADATA**<br />32 : **DISCOVER_TRACES**<br />33 : **DISCOVER_TRACE_DEFINITION_PROVIDERINFO**<br />34 : **DISCOVER_TRACE_COLUMNS**<br />35 : **DISCOVER_TRACE_EVENT_CATEGORIES**<br />36 : **DMSCHEMA_MINING_STRUCTURES**<br />37 : **DMSCHEMA_MINING_STRUCTURE_COLUMNS**<br />38 : **DISCOVER_MASTER_KEY**<br />39 : **MDSCHEMA_INPUT_DATASOURCES**<br />40 : **DISCOVER_LOCATIONS**<br />41 : **DISCOVER_PARTITION_DIMENSION_STAT**<br />42 : **DISCOVER_PARTITION_STAT**<br />43 : **DISCOVER_DIMENSION_STAT**<br />44 : **MDSCHEMA_MEASUREGROUP_DIMENSIONS**<br />45 : **DISCOVER_XEVENT_TRACE_DEFINITION**|  
|CurrentTime|2|5|Contient l'heure actuelle de l'événement de découverte, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Contient l'heure de début (le cas échéant) de l'événement de fin de découverte. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|EndTime|4|5|Contient l'heure de fin de l'événement. Cette colonne n'est pas remplie pour les classes d'événements de démarrage, comme SQL:BatchStarting ou SP:Starting. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|Duration|5|2|Contient la durée approximative (en millisecondes) de l'événement de découverte.|  
|CPUTime|6|2|Contient le temps processeur (en millisecondes) utilisé par l'événement.|  
|Severity|22| 1|Contient le niveau de gravité d'une exception.|  
|Réussi|23| 1|Contient la réussite ou l'échec de l'événement de découverte. Valeurs possibles :<br /><br /> 0 = Échec<br /><br /> 1 = Réussite|  
|Error|24| 1|Contient le nombre d'occurrences d'une erreur associée à l'événement de découverte.|  
|ConnectionID|25| 1|Contient l'ID de connexion unique associé à l'événement de découverte.|  
|DatabaseName|28|8|Contient le nom de la base de données dans laquelle l'événement de découverte s'est produit.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement d'autorisation de l'objet.|  
|NTDomainName|33|8|Contient le compte de domaine Windows associé à l'événement de découverte.|  
|ClientProcessID|36| 1|Contient l'ID de processus client de l'application qui a initialisé l'événement.|  
|ApplicationName|37|8|Contient le nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|Contient l'ID de session associé à l'événement de découverte.|  
|NTCanonicalUserName|40|8|Contient le nom d'utilisateur Windows associé à l'événement d'autorisation de l'objet. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|SPID|41| 1|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement de fin de découverte. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|TextData|42|9|Contient les données texte associées à l'événement.|  
|ServerName|43|8|Contient le nom de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l'événement de découverte s'est produit.|  
|RequestProperties|45|9|Contient les propriétés de la demande XMLA.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de découverte, catégorie d’événement](discover-events-event-category.md)  
  
  