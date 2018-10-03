---
title: TRUSTWORTHY, propriété de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: cb783b76e29ec77dd421fb3a73b34aa04dbb228d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850887"
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY, propriété de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La propriété de base de données TRUSTWORTHY permet d'indiquer si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] approuve la base de données et son contenu. Par défaut, cette propriété a la valeur OFF, mais peut être définie sur ON à l'aide de l'instruction ALTER DATABASE. Par exemple, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Pour définir cette option, vous devez être membre du rôle serveur fixe **sysadmin** .  
  
 Cette propriété permet de minimiser certaines menaces résultant de l'attachement d'une base de données contenant l'un des objets suivants :  
  
-   Assemblys malveillants dotés d'une autorisation EXTERNAL_ACCESS ou UNSAFE. Pour plus d’informations, consultez [Sécurité de l’intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
-   Modules malveillants définis dans le but de s'exécuter en tant qu'utilisateurs à privilèges élevés. Pour plus d’informations, consultez [Clause EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 Ces deux situations exigent un niveau spécifique de privilèges et sont mises en défaut par des mécanismes appropriés dès lors qu'elles sont utilisées dans le cadre d'une base de données déjà attachée à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, si la base de données est mise hors ligne, un utilisateur qui a accès au fichier de la base de données peut éventuellement l'attacher à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de son choix et ajouter un contenu malveillant à la base de données. En cas de détachement et d'attachement de bases de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certaines autorisations sont définies dans des fichiers de données et des fichiers journaux pour restreindre l'accès aux fichiers de la base de données.  
  
 Dans la mesure où il est impossible de faire immédiatement confiance à une base de données qui est attachée à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la base de données n'a pas le droit d'accéder aux ressources au-delà de son étendue tant qu'elle n'a pas été explicitement déclarée fiable. De plus, les modules conçus pour accéder aux ressources extérieures à la base de données et les assemblys dotés des autorisations EXTERNAL_ACCESS ou UNSAFE ont des impératifs supplémentaires à respecter pour pouvoir s'exécuter correctement.  
  
## <a name="related-content"></a>Contenu associé  
 [Centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
