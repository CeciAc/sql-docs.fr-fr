---
title: Interroge les colonnes de données d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Queries Events event category
ms.assetid: 28aa7df5-3e1f-4f4f-8a1c-8bbd29d5da13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 895a1cd168cd38d929c59024b5805fec413f3ec7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084529"
---
# <a name="queries-events-data-columns"></a>Colonnes de données des événements de requêtes
  La catégorie d'événement Événements de requête contient les classes d'événements suivantes :  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|Début de la requête.|  
|10|Query End|Fin de la requête.|  
  
 Les tableaux suivants répertorient les colonnes de données de chacune de ces classes d'événements.  
  
## <a name="query-begin-classdata-columns"></a>Classe Begin Query—Colonnes de données  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|EventSubclass|1|1|Sous-classes d’événements suivantes fournissent des informations supplémentaires sur chaque classe d’événements :<br /><br /> 0 : MDXQuery<br /><br /> 1 : DMXQuery<br /><br /> 2 : SQLQuery<br /><br /> 3 : DAXQuery|  
|CurrentTime|2|5|Contient l'heure actuelle de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Contient l'heure de début de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25|1|Contient l'ID de connexion unique associé à l'événement de requête.|  
|DatabaseName|28|8|Contient le nom de la base de données dans laquelle la requête est exécutée.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement de requête.|  
|NTDomainName|33|8|Contient le compte de domaine Windows associé à l'événement de requête.|  
|ClientProcessID|36|1|Contient l'ID de processus de l'application cliente.|  
|ApplicationName|37|8|Contient le nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|Contient l'ID de session unique de la requête XMLA.|  
|NTCanonicalUserName|40|8|Contient le nom d'utilisateur Windows associé à l'événement de requête. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|SPID|41|1|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement de requête. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|TextData|42|9|Contient les données texte associées à l'événement de requête.|  
|ServerName|43|8|Contient le nom de l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l’événement de requête s’est produit.|  
|RequestParameters|44|9|Contient les paramètres des requêtes paramétrables et commandes associées à l'événement de requête.|  
|RequestProperties|45|9|Contient les propriétés de la demande XMLA.|  
  
## <a name="query-end-classdata-columns"></a>Classe Query End—Colonnes de données  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|EventSubclass|1|1|Sous-classes d’événements suivantes fournissent des informations supplémentaires sur chaque classe d’événements.<br /><br /> 0 : MDXQuery<br /><br /> 1 : DMXQuery<br /><br /> 2 : SQLQuery<br /><br /> 3 : DAXQuery|  
|CurrentTime|2|5|Contient l'heure actuelle de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Contient l'heure de début de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|EndTime|4|5|Contient l'heure de fin de l'événement. Cette colonne n'est pas remplie pour les classes d'événements de démarrage, comme SQL:BatchStarting ou SP:Starting. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|Duration|5|2|Contient le temps (en millisecondes) pris par l'événement.|  
|CPUTime|6|2|Contient le temps processeur (en millisecondes) utilisé par l'événement.|  
|Severity|22|1|Contient le niveau de gravité d'une exception associée à l'événement de requête. Valeurs possibles :<br /><br /> 0 = Réussite<br /><br /> 1 = Informationnelle<br /><br /> 2 = Avertissement<br /><br /> 3 = Erreur|  
|Réussi|23|1|Contient la réussite ou l'échec de l'événement de requête. Valeurs possibles :<br /><br /> 0 = Échec<br /><br /> 1 = Réussite|  
|Error|24|1|Contient le nombre d'occurrences d'une erreur associée à l'événement de requête.|  
|ConnectionID|25|1|Contient l'ID de connexion unique associé à l'événement de requête.|  
|DatabaseName|28|8|Contient le nom de la base de données dans laquelle la requête est exécutée.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement de requête.|  
|NTDomainName|33|8|Contient le compte de domaine Windows associé à l'événement de requête.|  
|ClientProcessID|36|1|Contient l'ID de processus de l'application cliente.|  
|ApplicationName|37|8|Contient le nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|Contient l'ID de session unique de la requête XMLA.|  
|NTCanonicalUserName|40|8|Contient le nom d'utilisateur Windows associé à l'événement de requête. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|SPID|41|1|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement de requête. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|TextData|42|9|Contient les données texte associées à l'événement de requête.|  
|ServerName|43|8|Contient le nom de l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l’événement de requête s’est produit.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de requête, catégorie d’événement](queries-events-category.md)  
  
  
