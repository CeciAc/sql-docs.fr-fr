---
title: Création d’une chaîne de connexion valide avec TCP/IP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6449b073adb406d15f41cfe02d477a05ad8b0b31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63065495"
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a>Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP
  Pour créer une chaîne de connexion valide à l'aide du protocole TCP/IP, procédez comme suit :  
  
-   Spécifiez un **nom de l'alias**.  
  
-   Pour **Serveur**, entrez le nom d’un serveur auquel vous pouvez vous connecter à l’aide de l’utilitaire **PING** , ou une adresse IP à laquelle vous pouvez vous connecter au moyen de l’utilitaire **PING** . Pour une instance nommée, ajoutez le nom de l'instance.  
  
-   Spécifiez **TCP/IP** comme **Protocole**.  
  
-   Vous pouvez éventuellement entrer un numéro de port dans **Numéro de port**. La valeur par défaut est 1433 ; il s'agit du numéro de port de l'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur un serveur. Pour vous connecter à une instance nommée ou à une instance par défaut qui n'est pas à l'écoute sur le port 1433, vous devez spécifier le numéro de port ou démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser. Pour plus d’informations sur la configuration du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, consultez [Service SQL Server Browser](../../../2014/tools/configuration-manager/sql-server-browser-service.md).  
  
 Au moment de la connexion, le composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client lit dans le Registre les valeurs de serveur, protocole et port pour le nom d'alias spécifié, et crée une chaîne de connexion au format `tcp:<servername>[\<instancename>],<port>` ou `tcp:<IPAddress>[\<instancename>],<port>`.  
  
> [!NOTE]  
>  Le pare-feu [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ferme le port 1433 par défaut. Sachant que [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communique via le port 1433, vous devez rouvrir ce port si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour être à l’écoute des connexions clientes entrantes utilisant TCP/IP. Pour plus d’informations sur la configuration d’un pare-feu, consultez « Comment : Configurer un pare-feu pour accéder à SQL Server » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne ou passez en revue la documentation de votre pare-feu.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prennent intégralement en charge IPv4 (Internet Protocol version 4) et IPv6 (Internet Protocol version 6). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accepte les deux formats IPv4 et IPv6 pour les adresses IP. Pour plus d'informations sur IPv6, consultez « Connexion avec IPv6 » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="connecting-to-the-local-server"></a>Connexion au serveur local  
 Lorsque vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alors que celui-ci est exécuté sur le même ordinateur que l'ordinateur client, vous pouvez utiliser `(local)` comme nom de serveur. Cette option n'est pas conseillée dans la mesure où elle est source d'ambiguïté ; toutefois, elle peut s'avérer utile lorsqu'il est certain que le client s'exécute sur l'ordinateur visé. Par exemple, lorsque vous créez une application destinée à des utilisateurs itinérants déconnectés, tels que des vendeurs, pour lesquels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur des ordinateurs portables et stocke les données de projet, un client établissant une connexion à `(local)` se connecte toujours à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours d'exécution sur l'ordinateur portable. Vous pouvez utiliser le mot `localhost` ou un point ( **.** ) à la place de `(local)`.  
  
## <a name="verifying-your-connection-protocol"></a>Vérification de votre protocole de connexion  
 La requête suivante retourne le protocole utilisé pour la connexion active.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Exemples  
 Connexion à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Connexion à une instance nommée à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 Connexion à un port spécifié à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Connexion par l'adresse IP :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Connexion par l'adresse IP à une instance nommée :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 Connexion par l'adresse IP à un port spécifié :  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Connexion à l'ordinateur local à l'aide du paramètre `(local)`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 Connexion à l'ordinateur local à l'aide du paramètre `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 Connexion à une instance nommée sur l'ordinateur local `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 Connexion à l'ordinateur local à l'aide d'un point :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 Connexion à une instance nommée sur l'ordinateur local à l'aide d'un point :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  Pour plus d'informations sur la spécification du protocole réseau en tant que paramètre **sqlcmd**, consultez « Procédure : Se connecter au moteur de base de données à l’aide de sqlcmd.exe » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d'une chaîne de connexion valide à l'aide du protocole de mémoire partagée](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Création d'une chaîne de connexion valide à l'aide de canaux nommés](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)   
 [Choix d'un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
