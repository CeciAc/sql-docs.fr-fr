---
title: Planifier des packages SSIS dans Azure | Microsoft Docs
description: Fournit une vue d’ensemble des méthodes disponibles pour planifier l’exécution de packages SSIS déployés sur Azure SQL Database.
ms.date: 05/29/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: 4217acf163e8603c5993cfa8ade4207c9a79c6cf
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68054563"
---
# <a name="schedule-the-execution-of-sql-server-integration-services-ssis-packages-deployed-in-azure"></a>Planifier l’exécution de packages SSIS (SQL Server Integration Services) déployés dans Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Choisissez une des méthodes décrites dans cet article pour planifier l’exécution de packages SSIS déployés sur le catalogue SSISDB sur un serveur Azure SQL Database. Vous pouvez planifier un package soit directement, soit indirectement dans le cadre d’un pipeline Azure Data Factory. Pour obtenir une vue d’ensemble de SSIS sur Azure, consultez [Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud](ssis-azure-lift-shift-ssis-packages-overview.md).

- Planifier un package directement

  - [Planifier à l’aide de l’option Planifier dans SQL Server Management Studio (SSMS)](#ssms)

  - [Travaux élastiques SQL Database](#elastic)

  - [SQL Server Agent](#agent)

- [Planifier un package indirectement dans le cadre d’un pipeline Azure Data Factory](#activity)


## <a name="ssms"></a> Planifier un package avec SSMS

Dans SQL Server Management Studio (SSMS), vous pouvez cliquer avec le bouton droit sur un package déployé sur la base de données du catalogue SSIS, SSISDB, puis sélectionner **Planifier** pour ouvrir la boîte de dialogue **Nouvelle planification**. Pour plus d’informations, consultez [Planifier des packages SSIS dans Azure avec SSMS](ssis-azure-schedule-packages-ssms.md).

Cette fonctionnalité nécessite SQL Server Management Studio version 17.7 ou ultérieure. Pour obtenir la dernière version de SSMS, consultez [Télécharger SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="elastic"></a> Planifier un package avec des travaux élastiques SQL Database

Pour plus d’informations sur les travaux élastiques SQL Database, consultez [Gestion des bases de données cloud avec augmentation de la taille des instances](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Conditions préalables requises

Pour pouvoir utiliser des travaux élastiques afin de planifier des packages SSIS stockés dans la base de données de catalogues SSISDB sur un serveur Azure SQL Database, vous devez effectuer les actions suivantes :

1.  Installez et configurez les tâches de base de données élastique. Pour plus d’informations, consultez [Vue d’ensemble de l’installation des tâches de base de données élastique](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Créez des informations d’identification au niveau de la base de données pour permettre aux travaux d’envoyer des commandes à la base de données de catalogues SSIS. Pour plus d’informations, consultez [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Créer un travail élastique

Créez le travail à l’aide d’un script Transact-SQL similaire au script indiqué dans l’exemple suivant :

```sql
-- Create Elastic Jobs target groupÂ 
EXECÂ jobs.sp_add_target_group 'TargetGroup'Â 

-- Add Elastic Jobs target group memberÂ 
EXECÂ jobs.sp_add_target_group_memberÂ @target_group_name='TargetGroup',Â 
    @target_type='SqlDatabase',Â @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB'Â 

-- Add a job to schedule SSIS package execution
EXECÂ jobs.sp_add_jobÂ @job_name='ExecutePackageJob',Â @description='Description',Â 
    @schedule_interval_type='Minutes',Â @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXECÂ jobs.sp_add_jobstepÂ @job_name='ExecutePackageJob',Â 
    @command=N'DECLAREÂ @exe_idÂ bigintÂ 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1,Â 
            @execution_id=@exe_idÂ OUTPUT       Â 
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0',Â 
    @credential_name='YourDBScopedCredentials',Â 
    @target_group_name='TargetGroup'Â 

-- Enable the job scheduleÂ 
EXECÂ jobs.sp_update_jobÂ @job_name='ExecutePackageJob',Â @enabled=1,Â 
    @schedule_interval_type='Minutes',Â @schedule_interval_count=60Â 
```

## <a name="agent"></a> Planifier un package avec SQL Server Agent en local

Pour plus d’informations sur SQL Server Agent, consultez [Travaux de SQL Server Agent pour les packages](../packages/sql-server-agent-jobs-for-packages.md).

### <a name="prerequisite---create-a-linked-server"></a>Prérequis : Créer un serveur lié

Avant de pouvoir utiliser SQL Server Agent localement pour planifier l’exécution des packages stockés sur un serveur Azure SQL Database, vous devez ajouter le serveur SQL Database à votre serveur SQL Server local en tant que serveur lié.

1.  **Configurer le serveur lié**

    ```sql
    -- Add the SSISDB database on your Azure SQL Database as a linked server to your SQL Server on premises
    EXEC sp_addlinkedserver
        @server='myLinkedServer', -- Name your linked server
        @srvproduct='',     
        @provider='sqlncli', -- Use SQL Server native client
        @datasrc='<server_name>.database.windows.net', -- Add your Azure SQL Database server endpoint
        @location='',
        @provstr='',
        @catalog='SSISDB'  -- Add SSISDB as the initial catalog
    ```

2.  **Configurer les informations d’identification du serveur lié**

    ```sql
    -- Add your Azure SQL DB server admin credentials
    EXEC sp_addlinkedsrvlogin
        @rmtsrvname = 'myLinkedServer',
        @useself = 'false',
        @rmtuser = 'myUsername', -- Add your server admin username
        @rmtpassword = 'myPassword' -- Add your server admin password
    ```

3.  **Configurer les options du serveur lié**

    ```sql
    EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;
    ```

Pour plus d’informations, consultez [Créer des serveurs liés](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) et [Serveurs liés](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Créer un travail de SQL Server Agent

Pour planifier un package avec SQL Server Agent localement, créez un travail avec une étape de travail qui appelle les procédures stockées du catalogue SSIS `[catalog].[create_execution]`, puis `[catalog].[start_execution]`. Pour plus d’informations, consultez [Travaux de SQL Server Agent pour les packages](../packages/sql-server-agent-jobs-for-packages.md).

1.  Dans SQL Server Management Studio, connectez-vous à la base de données SQL Server locale sur laquelle vous souhaitez créer le travail.

2.  Cliquez avec le bouton droit sur le nœud **SQL Server Agent**, sélectionnez **Nouveau**, puis **Travail** pour ouvrir la boîte de dialogue **Nouveau travail**.

3.  Dans la boîte de dialogue **Nouveau travail**, sélectionnez la page **Étapes**, puis **Nouveau** pour ouvrir la boîte de dialogue **Nouvelle étape du travail**.

4.  Dans la boîte de dialogue **Nouvelle étape du travail**, sélectionnez `SSISDB` en tant que **Base de données**.

5.  Dans le champ **Commande**, entrez un script Transact-SQL similaire au script figurant dans l’exemple suivant :

    ```sql
    -- T-SQL script to create and start SSIS package execution using SSISDB stored procedures
    DECLARE @return_valueÂ int,Â @exe_idÂ bigintÂ 

    EXEC @return_valueÂ =Â [YourLinkedServer].[SSISDB].[catalog].[create_execution]Â 
        @folder_name=N'folderName',Â @project_name=N'projectName',Â 
        @package_name=N'packageName',Â @use32bitruntime=0,Â @runincluster=1,Â @useanyworker=1,
        @execution_id=@exe_idÂ OUTPUTÂ 

    EXEC [YourLinkedServer].[SSISDB].[catalog].[set_execution_parameter_value] @exe_id,
        @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution]Â @execution_id=@exe_id
    ```

6.  Finissez de configurer et de planifier le travail.

## <a name="activity"></a> Planifier un package dans le cadre d’un pipeline Azure Data Factory

Vous pouvez planifier un package indirectement à l’aide d’un déclencheur pour exécuter un pipeline Azure Data Factory qui exécute un package SSIS.

Pour planifier un pipeline Data Factory, utilisez l’un des déclencheurs suivants :

- [Déclencheur de planification](https://docs.microsoft.com/azure/data-factory/how-to-create-schedule-trigger)

- [Déclencheur de fenêtre bascule](https://docs.microsoft.com/azure/data-factory/how-to-create-tumbling-window-trigger)

- [Déclencheur basé sur un événement](https://docs.microsoft.com/azure/data-factory/how-to-create-event-trigger)

Pour exécuter un package SSIS dans le cadre d’un pipeline Data Factory, utilisez l’une des activités suivantes :

- [Activité Exécuter le package SSIS](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

- [Activité Procédure stockée](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity).

## <a name="next-steps"></a>Étapes suivantes

Passez en revue les options disponibles pour exécuter des packages SSIS déployés sur Azure. Pour plus d’informations, consultez [Exécuter des packages SSIS dans Azure](ssis-azure-run-packages.md).
