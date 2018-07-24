---
title: Applets de commande PowerShell pour Reporting Services SharePoint Mode | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 29a9177685d94be437574e90a44a46a2391bcba7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311361"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>Applets de commande PowerShell pour le mode SharePoint de Reporting Services
  Lorsque vous installez le mode SharePoint de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , les applets de commande PowerShell sont installées pour prendre en charge les serveurs de rapports en mode SharePoint. Les applets de commande couvrent trois catégories de fonctionnalités.  
  
-   Installation de le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint service partagé et proxy.  
  
-   Configuration et gestion de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applications de service et proxys associés.  
  
-   Gestion des fonctionnalités d' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , par exemple extensions et clés de chiffrement.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint|  
  
 **Cette rubrique contient les sections suivantes :**  
  
-   [Résumé des applets de commande](#bkmk_cmdlet_sum)  
  
-   [Applets de commande de service partagé et de proxy](#bkmk_sharedservice_cmdlets)  
  
-   [Applets de commande d'application de service et de proxy](#bkmk_serviceapp_cmdlets)  
  
-   [Applets de commande personnalisés de la fonctionnalité « Reporting Services »](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Exemples de base](#bkmk_basic_samples)  
  
-   [Exemples détaillés](#bkmk_detailedsamples)  
  
    -   [Créer une application de service Reporting Services et un proxy](#bkmk_example_create_service_application)  
  
    -   [Passez en revue et mettre à jour une extension de remise de Reporting Services](#bkmk_example_delivery_extension)  
  
    -   [Obtenir et définir les propriétés de la base de données de l’application du Reporting Services, par exemple délai d’attente de base de données](#bkmk_example_db_properties)  
  
    -   [Liste des extensions de données reporting services – mode SharePoint](#bkmk_example_list_data_extensions)  
  
    -   [Modifier et répertorier les propriétaires d’abonnements](#bkmk_change_subscription_owner)  
  
##  <a name="bkmk_cmdlet_sum"></a> Résumé des applets de commande  
 Pour exécuter les applets de commande, vous devez ouvrir SharePoint Management Shell. Vous pouvez aussi utiliser l’éditeur d’interface utilisateur graphique fourni avec Microsoft Windows : **l’Environnement d’écriture de scripts intégré de Windows PowerShell (ISE)**. Pour plus d’informations, consultez [démarrage de Windows PowerShell sur Windows Server](http://technet.microsoft.com/library/hh847814.aspx) (http://technet.microsoft.com/library/hh847814.aspx). Dans les résumés suivants d'applets de commande, les références à l'application de service « bases de données » font référence à toutes les bases de données créées et utilisées par une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Cela inclut la configuration, la définition d'alertes et les bases de données temp.  
  
 Si vous voyez un message d'erreur semblable au suivant lorsque vous tapez les exemples PowerShell :  
  
-   Install-SPRSService : Le terme 'Install-SPRSService' n'est pas reconnu comme  
    nom d'applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l'orthographe du nom, ou si un chemin d'accès existe, vérifiez que le chemin d'accès est correct et réessayez.  
  
 Un des problèmes suivants se produit :  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Mode SharePoint n’est pas installé et par conséquent le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applets de commande ne sont pas installés.  
  
-   Vous avez exécuté la commande PowerShell dans Windows PowerShell ou Windows PowerShell ISE au lieu de SharePoint Management Shell. Utilisez SharePoint Management Shell ou ajoutez le composant logiciel enfichable SharePoint à la fenêtre Windows PowerShell à l'aide de la commande suivante :  
  
    ```  
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Pour plus d’informations, consultez [utiliser Windows PowerShell pour administrer SharePoint 2013](http://technet.microsoft.com/library/ee806878.aspx) (http://technet.microsoft.com/library/ee806878.aspx).  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>Pour ouvrir SharePoint Management Shell et exécuter les applets de commande  
  
1.  Cliquez sur le bouton **Démarrer** .  
  
2.  Cliquez sur le groupe **Produits Microsoft SharePoint** .  
  
3.  Cliquez sur **SharePoint Management Shell**.  
  
 Pour consulter l'aide sur la ligne de commande pour une applet de commande utilisez la commande « GET-HELP » de PowerShell à l'invite de commandes de PowerShell. Exemple :  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="bkmk_sharedservice_cmdlets"></a> Applets de commande de service partagé et de proxy  
 Le tableau suivant contient les applets de commande PowerShell pour le service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint.  
  
|Applet de commande|Description|  
|------------|-----------------|  
|Install-SPRSService|Installe et enregistre, ou désinstalle, le service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Cette opération peut être effectuée uniquement sur l'ordinateur qui dispose d'une installation de SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint. Pour l'installation, deux opérations ont lieu :<br /><br /> (1) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service est installé dans la batterie de serveurs.<br /><br /> (2) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance de service est installée sur l’ordinateur actuel.<br /><br /> Pour la désinstallation, deux opérations ont lieu :<br />(1) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service est désinstallé de l’ordinateur actuel.<br />(2) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service est désinstallé de la batterie de serveurs.<br /><br /> <br /><br /> Remarque : S’il existe d’autres ordinateurs dans la batterie de serveurs qui ont le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service installé, ou s’il existe toujours [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] les applications de service en cours d’exécution dans la batterie de serveurs, un message d’avertissement s’affiche.|  
|Install-SPRSServiceProxy|Installe et enregistre, ou désinstalle, le proxy du service Reporting Services dans la batterie de serveurs SharePoint.|  
|Get-SPRSProxyUrl|Obtient les URL pour accéder à la [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service.|  
|Get-SPRSServiceApplicationServers|Obtient tous les serveurs dans la batterie SharePoint locale qui contiennent une installation du service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Cette applet de commande est utile pour les mises à niveau de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , car elle permet de déterminer quels serveurs exécutent le service partagé et doivent, par conséquent, être mis à niveau.|  
  
###  <a name="bkmk_serviceapp_cmdlets"></a> Applets de commande d'application de service et de proxy  
 Le tableau suivant contient les applets de commande PowerShell pour les applications de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et leurs proxys associés.  
  
|Applet de commande|Description|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Obtient un ou plusieurs objets d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|New-SPRSServiceApplication|Crée une application de service Reporting Services et des bases de données associées.<br /><br /> Paramètre LogonType : spécifie si le serveur de rapports utilise le compte de pool d'applications SSRS ou un compte de connexion SQL Server pour accéder à la base de données du serveur de rapports. Les valeurs possibles sont les suivantes :<br /><br /> 0 Authentification Windows<br /><br /> 1 SQL Server<br /><br /> 2. Compte du pool d'applications (valeur par défaut)|  
|Remove-SPRSServiceApplication|Supprime l'application de service Reporting Services spécifiée. Cela supprimera également les bases de données associées.|  
|Set-SPRSServiceApplication|Modifie les propriétés d'une base de données d'application de service Reporting Services existante.|  
|New-SPRSServiceApplicationProxy|Crée un nouveau proxy d'application de service Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Obtient un ou plusieurs [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxys d’application de service.|  
|Dismount-SPRSDatabase|Démonte les bases de données d'application de service pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|Remove-SPRSDatabase|Supprimer les bases de données pour un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application de service.|  
|Set-SPRSDatabase|Définit les propriétés des bases de données associées à une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|Mount-SPRSDatabase|Monte les bases de données pour un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application de service.|  
|New-SPRSDatabase|Créer de nouvelles bases de données spécifié [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application de service.|  
|Get-SPRSDatabaseCreationScript|Génère le script de création de base de données à l'écran pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Vous pouvez ensuite exécuter le script dans SQL Server Management Studio.|  
|Get-SPRSDatabase|Obtient une ou plusieurs bases de données d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Utilisez la commande pour obtenir l'ID de la base de données d'application de service afin d'utiliser l'applet de commande Set-SPRSDatabase pour modifier les propriétés, par exemple `querytimeout`. Consultez l'exemple de la rubrique, [Obtenir et définir les propriétés de la base de données d'application Reporting Services, par exemple le délai d'expiration de la base de données](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Génère le script de droits de base de données à l’écran pour un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application de service. Invite à entrer l'utilisateur et la base de données souhaités, puis retourne un script Transact-SQL que vous pouvez exécuter pour modifier des autorisations. Vous pouvez ensuite exécuter ce script dans SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Génère un script de mise à niveau de base de données à l'écran. Le script met à niveau les bases de données d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] vers la version de la base de données de l'installation actuelle de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
  
###  <a name="bkmk_ssrsfeatures_cmdlets"></a> Applets de commande personnalisés de la fonctionnalité « Reporting Services »  
  
|Applet de commande|Description|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Met à jour la clé de chiffrement de l'application de service Reporting Services spécifiée et re-chiffre ses données.|  
|Restore-SPRSEncryptionKey|Restaure une clé de chiffrement précédemment sauvegardée pour une application de service Reporting Services.|  
|Remove-SPRSEncryptedData|Supprime les données chiffrées de l'application de service Reporting Services spécifiée.|  
|Backup-SPRSEncryptionKey|Sauvegarde la clé de chiffrement de l'application de service Reporting Services spécifiée.|  
|New-SPRSExtension|Enregistre une nouvelle extension avec une application de service Reporting Services.|  
|Set-SPRSExtension|Définit les propriétés d'une extension Reporting Services existante.|  
|Remove-SPRSExtension|Supprime une extension d'une application de service Reporting Services.|  
|Get-SPRSExtension|Obtient un ou plusieurs [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] extensions pour un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application de service.<br /><br /> Les valeurs valides sont :<br /><br /> **Remise**<br /><br /> **DeliveryUI**<br /><br /> **Render**<br /><br /> **Data**<br /><br /> **Sécurité**<br /><br /> **Authentification**<br /><br /> **EventProcessing**<br /><br /> **ReportItems**<br /><br /> **Designer**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Obtient les sites SharePoint en fonction de l'activation de la fonction « ReportingService ». Par défaut, les sites qui activent la fonction « ReportingService » sont retournés.|  
  
##  <a name="bkmk_basic_samples"></a> Exemples de base  
 Retournez la liste des applets de commande qui contiennent « SPRS » dans le nom. Il s’agit de la liste complète des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applets de commande.  
  
```  
Get-command –noun *SPRS*  
```  
  
 Ou bien, vous serez redirigés vers un fichier texte nommé commandlist.txt contenant plus de détails.  
  
```  
Get-command -noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Installez le service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint et le proxy de service.  
  
```  
Install-SPRSService  
```  
  
```  
Install-SPRSServiceProxy  
```  
  
 Démarrer le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service  
  
```  
get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Tapez la commande suivante à partir de SharePoint Management Shell pour retourner une liste filtrée des lignes du fichier journal. La commande filtre les lignes qui contiennent « ssrscustomactionerror ». Cet exemple consulte le fichier journal créé lorsque le fichier rssharepoint.msi a été installé.  
  
```  
Get-content -path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
```  
  
##  <a name="bkmk_detailedsamples"></a> Exemples détaillés  
 Outre les exemples suivants, consultez la section « Script Windows PowerShell » dans la rubrique [Windows PowerShell script for Steps 1–4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="bkmk_example_create_service_application"></a> Créer une application de service Reporting Services et un proxy  
 Cet exemple de script effectue les tâches suivantes :  
  
1.  Création d'une application de service Reporting Services et d'un proxy. Le script suppose que le pool d'applications « My App Pool » existe déjà.  
  
2.  Ajout du proxy au groupe de proxy par défaut  
  
3.  Octroi de l'accès aux applications de service à la base de données de contenus de l'application Web sur le port 80. Le script considère que le site «http://sitename» existe déjà.  
  
```  
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool “My App Pool”  
$serviceApp = New-SPRSServiceApplication “My RS Service App” –ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy –Name “My RS Service App Proxy” –ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup –default | Add-SPServiceApplicationProxyGroupMember –Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application’s content database.  
$webApp = Get-SPWebApplication “http://sitename”  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)  
  
```  
  
###  <a name="bkmk_example_delivery_extension"></a> Passez en revue et mettre à jour une extension de remise de Reporting Services  
 L’exemple de script PowerShell suivant met à jour la configuration de l’extension de remise du courrier électronique par le serveur de rapports pour l’application de service nommée `My RS Service App`. Mettez à jour les valeurs du serveur SMTP (`<email server name>`) et de l’alias de messagerie électronique FROM (`<your FROM email address>`).  
  
```  
$app=get-sprsserviceapplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
$emailXml = [xml]$emailCfg   
$emailXml.SelectSingleNode("//SMTPServer").InnerText = “<email server name>”  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 Dans l'exemple ci-dessus, si vous ne connaissiez pas le nom exact de l'application de service, vous pouvez réécrire la première instruction pour obtenir l'application de service en fonction d'une recherche portant sur son nom partiel. Exemple :  
  
```  
$app=get-sprsserviceapplication | where {$_.name -like " ssrs_testapp *"}  
```  
  
 Le script suivant retourne les valeurs de configuration actuelles pour l'extension de remise de courrier électronique du serveur de rapports pour l'application de service nommée « Application Reporting Services ». La première étape définit la valeur de la variable $app pour l'objet de l'application de service dont le nom est « My RS Service App ».  
  
 La deuxième instruction obtiendra l'extension de remise « Report Server Email » pour l'objet d'application de service dans la variable $app, puis sélectionne le configuration XML.  
  
```  
$app=get-sprsserviceapplication –Name "Reporting Services Application"  
Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
 Vous pouvez réécrire les deux instructions ci-dessus dans une seule :  
  
```  
get-sprsserviceapplication –Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="bkmk_example_db_properties"></a> Obtenir et définir les propriétés de la base de données de l’application du Reporting Services, par exemple délai d’attente de base de données  
 L'exemple suivant renvoie d'abord une liste des bases de données et propriétés afin de déterminer le guid (ID) de base de données que vous fournissez à la commande. Pour obtenir une liste complète des propriétés, utilisez `Get-SPRSDatabase | format-list`.  
  
```  
get-SPRSDatabase | select id, querytimeout,connectiontimeout, status, server, ServiceInstance   
```  
  
 Voici un exemple de sortie. Déterminez l'ID de la base de données que vous voulez modifier et utilisez l'ID de l'applet de commande SET.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```  
Set-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Pour vérifier que la valeur est définie, réexécutez l'applet de commande GET.  
  
```  
Get-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="bkmk_example_list_data_extensions"></a> Liste des extensions de données reporting services – mode SharePoint  
 L'exemple suivant effectue une itération sur chaque application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et répertorie les extensions de données actuelles.  
  
```  
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)   
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType “Data” | select name,extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Exemple de sortie :**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="bkmk_change_subscription_owner"></a> Modifier et répertorier les propriétaires d’abonnements  
 Consultez [Utiliser PowerShell pour modifier et répertorier les propriétaires d’abonnements Reporting Services, et exécuter un abonnement](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser PowerShell pour modifier et répertorier les propriétaires d’abonnements Reporting Services et exécuter un abonnement](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Liste de vérification : Utiliser PowerShell pour vérifier PowerPivot pour SharePoint](../analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)   
 [Scripts PowerShell de gestion CodePlex SharePoint](http://sharepointpsscripts.codeplex.com/)   
 [Comment administrer SSRS à l’aide de PowerShell](https://curatedviews.cloudapp.net/13107/how-to-administer-ssrs-using-powershell)  
  
  