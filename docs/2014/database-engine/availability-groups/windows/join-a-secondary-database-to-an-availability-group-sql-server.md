---
title: Joindre une base de données secondaire à un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5de4600d4f4c3d52d1757218e1f2d9b32f554286
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797673"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>Joindre une base de données secondaire à un groupe de disponibilité (SQL Server)
  Cette rubrique explique comment joindre une base de données secondaire à un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Après avoir préparé une base de données secondaire pour un réplica secondaire, vous devez joindre la base de données au groupe de disponibilité dès que possible. Cette opération lance le déplacement des données entre la base de données primaire correspondante et la base de données secondaire.  
  
-   **Avant de commencer :**  
  
     [Prérequis](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour préparer une base de données secondaire, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Pour plus d’informations sur ce qui se produit après qu’une base de données secondaire a rejoint le groupe, consultez [vue d’ensemble de &#40;groupes de disponibilité AlwaysOn SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables requises  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica secondaire.  
  
-   Le réplica secondaire doit déjà être joint au groupe de disponibilité. Pour plus d’informations, consultez [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
-   La base de données secondaire doit avoir été préparée récemment. Pour plus d’informations, consultez [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour joindre une base de données secondaire à un groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica secondaire et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Développez le groupe de disponibilité que vous souhaitez modifier, puis développez le nœud **Bases de données de disponibilité** .  
  
4.  Cliquez avec le bouton droit sur la base de données, puis cliquez sur **Joindre au groupe de disponibilité**.  
  
5.  Cette opération ouvre la boîte de dialogue **Joindre les bases de données au groupe de disponibilité** . Vérifiez le nom du groupe de disponibilité affiché dans la barre de titre, ainsi que le nom de la ou des bases de données affichées dans la grille, puis cliquez sur **OK**, ou cliquez sur **Annuler**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour joindre une base de données secondaire à un groupe de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica secondaire.  
  
2.  Utilisez la [clause SET HADR de l'instruction ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) comme suit :  
  
     ALTER DATABASE *nom_base_de_données* SET HADR AVAILABILITY GROUP = *nom_groupe*  
  
     où *nom_base_de_données* est le nom d’une base de données à joindre et *nom_groupe* est le nom du groupe de disponibilité .  
  
     L'exemple suivant joint la base de données secondaire, `Db1`, au réplica secondaire local du groupe de disponibilité `MyAG`.  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Pour consulter cette instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] utilisée en contexte, consultez [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour joindre une base de données secondaire à un groupe de disponibilité**  
  
1.  Remplacez le répertoire (`cd`) par l'instance de serveur qui héberge le réplica secondaire.  
  
2.  Utilisez l'applet de commande `Add-SqlAvailabilityDatabase` pour joindre une ou plusieurs bases de données secondaires au groupe de disponibilité.  
  
     Par exemple, la commande suivante joint une base de données secondaire, `Db1`, au groupe de disponibilité `MyAG` sur l'une des instances de serveur qui héberge un réplica secondaire.  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour plus d’informations, consultez [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [fournisseur PowerShell SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Tâches connexes  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Vue d’ensemble &#40;de&#41; groupes de disponibilité AlwaysOn SQL Server](overview-of-always-on-availability-groups-sql-server.md)   
 [Résoudre les problèmes &#40;de&#41;configuration de groupes de disponibilité AlwaysOn SQL Server supprimés](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
