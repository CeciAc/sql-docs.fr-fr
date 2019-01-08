---
title: sysmail_update_account_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_account_sp
- sysmail_update_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_account_sp
ms.assetid: ba2fdccc-5ed4-40ef-a479-79497b4d61aa
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 86de9f970713d84fec0722a4cc3c29b0b307098f
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589944"
---
# <a name="sysmailupdateaccountsp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les informations dans un compte de messagerie de base de données existant.  
 
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_update_account_sp [ [ @account_id = ] account_id ] [ , ] [ [ @account_name = ] 'account_name' ] ,  
    [ @email_address = ] 'email_address' ,   
    [ @display_name = ] 'display_name' ,   
    [ @replyto_address = ] 'replyto_address' ,  
    [ @description = ] 'description' ,   
    [ @mailserver_name = ] 'server_name' ,   
    [ @mailserver_type = ] 'server_type' ,   
    [ @port = ] port_number ,   
    [ @timeout = ] 'timeout' ,  
    [ @username = ] 'username' ,  
    [ @password = ] 'password' ,  
    [ @use_default_credentials = ] use_default_credentials ,  
    [ @enable_ssl = ] enable_ssl   
```  
  
## <a name="arguments"></a>Arguments  
 [ **@account_id** =] *account_id*  
 ID du compte à mettre à jour. *account_id* est **int**, avec NULL comme valeur par défaut. Au moins une des *account_id* ou *account_name* doit être spécifié. Si les deux arguments sont précisés, la procédure modifie le nom du compte.  
  
 [ **@account_name** =] **'**_account_name_**'**  
 Nom du compte à mettre à jour. *nom_compte* est **sysname**, avec NULL comme valeur par défaut. Au moins une des *account_id* ou *account_name* doit être spécifié. Si les deux arguments sont précisés, la procédure modifie le nom du compte.  
  
 [ **@email_address** =] **'**_email_address_**'**  
 Nouvelle adresse de messagerie d'où le message est envoyé. Cette adresse doit être une adresse de messagerie Internet. Le nom de serveur figurant dans l'adresse identifie le serveur qu'utilise la messagerie de base de données pour envoyer le courrier à partir de ce compte. *email_address* est **nvarchar (128)**, avec NULL comme valeur par défaut.  
  
 [ **@display_name** =] **'**_display_name_**'**  
 Nouveau nom complet à utiliser sur des messages électroniques à partir de ce compte. *display_name* est **nvarchar (128)**, sans valeur par défaut.  
  
 [ **@replyto_address** =] **'**_replyto_address_**'**  
 Nouvelle adresse à utiliser dans le champ « Répondre à » des messages électroniques envoyés à partir de ce compte. *replyto_address* est **nvarchar (128)**, sans valeur par défaut.  
  
 [ **@description** =] **'**_description_**'**  
 Nouvelle description du compte. *Description* est **nvarchar (256)**, avec NULL comme valeur par défaut.  
  
 [ **@mailserver_name** =] **'**_nom_serveur_**'**  
 Nouveau nom de serveur de messagerie SMTP à utiliser pour ce compte. L’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en mesure de résoudre le *nom_serveur* à une adresse IP. *nom_serveur* est **sysname**, sans valeur par défaut.  
  
 [ **@mailserver_type** =] **'**_server_type_**'**  
 Nouveau type du serveur de messagerie. *server_type* est **sysname**, sans valeur par défaut. Seule la valeur **'SMTP'** est pris en charge.  
  
 [ **@port** =] *numéro_port*  
 Nouveau numéro de port du serveur de messagerie. *numéro_port* est **int**, sans valeur par défaut.  
  
 [ **@timeout** =] **'**_délai d’attente_**'**  
 Paramètre Timeout pour SmtpClient.Send d'un message e-mail. *Délai d’attente* est **int** en quelques secondes, sans valeur par défaut.  
  
 [ **@username** =] **'**_nom d’utilisateur_**'**  
 Nouveau nom d'utilisateur servant lors de la connexion au serveur de messagerie. *Nom d’utilisateur* est **sysname**, sans valeur par défaut.  
  
 [ **@password** =] **'**_mot de passe_**'**  
 Nouveau mot de passe servant lors de la connexion au serveur de messagerie. *mot de passe* est **sysname**, sans valeur par défaut.  
  
 [ **@use_default_credentials** =] use_default_credentials  
 Spécifie si le courrier électronique doit être envoyé au serveur SMTP en utilisant les informations d'identification du service [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** est de type bit, sans valeur par défaut. Lorsque la valeur de ce paramètre est définie sur 1, la messagerie de base de données utilise les informations d'identification du moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Lorsque ce paramètre est 0, la messagerie de base de données utilise le **@username** et **@password** pour l’authentification sur le serveur SMTP. Si **@username** et **@password** ont la valeur NULL, puis il utilise l’authentification anonyme. Contactez votre administrateur SMTP avant de définir ce paramètre.  
  
 [ **@enable_ssl** =] enable_ssl  
 Spécifie si la messagerie de base de données chiffre les communications à l'aide de la technologie SSL (Secure Sockets Layer). Utilisez cette option si SSL est obligatoire sur votre serveur SMTP. **enable_ssl** est de type bit, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Lorsque le nom et l'ID du compte sont tous deux spécifiés, la procédure stockée change le nom du compte en plus de mettre à jour les autres informations du compte. Il peut s'avérer nécessaire de modifier le nom du compte pour corriger des erreurs qui s'y seraient glissées.  
  
 La procédure stockée **sysmail_update_account_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-information-for-an-account"></a>A. Modification des informations d'un compte  
 L’exemple suivant met à jour le compte `AdventureWorks Administrator` dans le **msdb** base de données. Les informations du compte prennent les valeurs fournies.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_name = 'AdventureWorks Administrator'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>b. Modification du nom d'un compte et des informations qui s'y rapportent  
 L'exemple suivant modifie le nom du compte et le met à jour avec l'ID de compte `125`. Le nouveau nom du compte est `Backup Mail Server`.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_id = 125  
    ,@account_name = 'Backup Mail Server'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp-backup.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
