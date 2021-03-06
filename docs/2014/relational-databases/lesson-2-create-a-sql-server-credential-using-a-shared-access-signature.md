---
title: 'Leçon 3 : Créer des informations d’identification de SQL Server | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 61a25d1f4e86204d05b3be6bf2a5dbc8cd0474b9
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153832"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Leçon 3 : Créer des informations d'identification SQL Server
  Dans cette leçon, vous allez créer des informations d’identification pour stocker les informations de sécurité utilisées pour accéder au compte de stockage Azure.  
  
 Les informations d'identification SQL Server sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server. Les informations d'identification contiennent le chemin d'accès de l'URI du conteneur de stockage et les valeurs de clé de signature d'accès partagé. Pour chaque conteneur de stockage utilisé par un fichier de données ou un fichier journal, vous devez créer des informations d'identification SQL Server dont le nom correspond au chemin d'accès du conteneur.  
  
 Pour obtenir des informations générales sur les informations d’identification, consultez [informations d’identification &#40;&#41;moteur de base de données](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  La configuration requise pour la création d’une SQL Server informations d’identification décrites ci-dessous sont spécifiques à la fonctionnalité [fichiers de données SQL Server dans Azure](databases/sql-server-data-files-in-microsoft-azure.md) . Pour plus d’informations sur la création d’informations d’identification pour les processus [de sauvegarde dans le stockage Azure, consultez la leçon 2: Créez un SQL Server des](../tutorials/lesson-2-create-a-sql-server-credential.md)informations d’identification.  
  
 Pour créer des informations d'identification SQL Server, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Dans l'Explorateur d'objets, connectez-vous à l'instance du moteur de base de données installée.  
  
3.  Dans la barre d'outils standard, cliquez sur Nouvelle requête.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire. L’instruction suivante crée un SQL Server informations d’identification pour stocker le certificat d’accès partagé de votre conteneur de stockage.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Pour plus d’informations, consultez [créer &#40;des informations d'&#41; identification Transact-SQL](/sql/t-sql/statements/create-credential-transact-sql) dans documentation en ligne de SQL Server.  
  
5.  Pour voir toutes les informations d'identification disponibles, exécutez l'instruction suivante dans la fenêtre de requête :  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Pour plus d’informations sur sys. Credentials, consultez [sys. Credentials &#40;Transact-&#41; SQL](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) dans documentation en ligne de SQL Server.  
  
 **Leçon suivante :**  
  
 [Leçon 4 : Créer une base de données dans Azure Storage](lesson-3-database-backup-to-url.md)  
  
  
