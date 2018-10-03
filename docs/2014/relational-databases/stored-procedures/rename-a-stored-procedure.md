---
title: Renommer une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a6cc6f8ca0c5bb6657cd26350267f557edd014be
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092429"
---
# <a name="rename-a-stored-procedure"></a>Renommer une procédure stockée
  Cette rubrique explique comment renommer une procédure stockée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour renommer une procédure stockée à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les noms des procédures doivent respecter les conventions concernant les [identificateurs](../databases/database-identifiers.md).  
  
-   Le fait de renommer une procédure stockée ne modifie pas le nom de l’objet correspondant dans la colonne de définition de l’affichage catalogue **sys.sql_modules** . Par conséquent, nous vous recommandons de ne pas renommer ce type d'objet. À la place, supprimez, puis recréez la procédure stockée avec son nouveau nom.  
  
-   La modification du nom ou de la définition d'une procédure peut entraîner l'échec de ses objets dépendants si ceux-ci n'ont pas été mis à jour pour refléter les modifications apportées à la procédure. Pour plus d’informations, consultez [Afficher les dépendances d’une procédure stockée](view-the-dependencies-of-a-stored-procedure.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 CREATE PROCEDURE  
 Nécessite l’autorisation CREATE PROCEDURE dans la base de données et l’autorisation ALTER sur le schéma dans lequel la procédure est créée, ou nécessite l’appartenance au rôle de base de données fixe **db_ddladmin** .  
  
 ALTER PROCEDURE  
 Requiert l’autorisation ALTER sur la procédure ou l’appartenance au rôle de base de données fixe **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-rename-a-stored-procedure"></a>Pour renommer une procédure stockée  
  
1.  Dans l’Explorateur d’objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure, puis développez **Programmabilité**.  
  
3.  [Déterminez les dépendances de la procédure stockée](view-the-dependencies-of-a-stored-procedure.md).  
  
4.  Développez **Procédures stockées**, cliquez avec le bouton droit sur la procédure à renommer, puis cliquez sur **Renommer**.  
  
5.  Modifiez le nom de la procédure.  
  
6.  Modifiez le nom de la procédure référencé dans tous les objets ou scripts dépendants.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-rename-a-stored-procedure"></a>Pour renommer une procédure stockée  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment renommer une procédure en la supprimant puis en la recréant avec un nouveau nom. Le premier exemple crée la procédure stockée `'HumanResources.uspGetAllEmployeesTest`. Le deuxième exemple renomme la procédure stockée en `HumanResources.uspEveryEmployeeTest`.  
  
```tsql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)   
 [Créer une procédure stockée](../stored-procedures/create-a-stored-procedure.md)   
 [Modifier une procédure stockée](../stored-procedures/modify-a-stored-procedure.md)   
 [Supprimer une procédure stockée](../stored-procedures/delete-a-stored-procedure.md)   
 [Afficher la définition d'une procédure stockée](view-the-definition-of-a-stored-procedure.md)   
 [Afficher les dépendances d’une procédure stockée](view-the-dependencies-of-a-stored-procedure.md)  
  
  
