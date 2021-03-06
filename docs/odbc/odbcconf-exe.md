---
title: ODBCCONF. EXE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b70622ea038b61883ce7a5307a558a5667139fb1
ms.sourcegitcommit: a26cb217adfbbfb3636dff43fb19a46462e2e994
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491963"
---
# <a name="odbcconfexe"></a>ODBCCONF. EXÉCUTABLE
ODBCCONF. exe est un outil de ligne de commande qui vous permet de configurer des pilotes ODBC et des noms de sources de données.  
  
> [!NOTE]  
>  ODBCCONF. exe sera supprimé dans une future version des composants d’accès aux données Windows. Évitez d’utiliser cette fonctionnalité et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Vous pouvez utiliser des commandes PowerShell pour gérer des pilotes et des sources de données. Pour plus d’informations sur ces commandes PowerShell, consultez applets de commande des [composants d’accès aux données Windows](/powershell/module/wdac).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Arguments  
 *Active*  
 Zéro, une ou plusieurs options de commutateur. Pour obtenir la liste des commutateurs disponibles, consultez la section Notes, plus loin dans cette rubrique.  
  
 *transactionnel*  
 Une action à effectuer. Pour obtenir la liste des options disponibles, consultez la section Notes.  
  
## <a name="remarks"></a>Remarques  
 Les commutateurs suivants sont disponibles :  
  
|Commutateur|Description|  
|------------|-----------------|  
|/A {*action*}|Spécifiez une action.<br /><br /> /A est facultatif si une seule action est spécifiée.|  
|/?|Affichez l’utilisation de ODBCCONF. Exécutable.|  
|Commutateur|Le traitement se poursuit en cas d’échec d’une action.|  
|/E|Efface le fichier réponse spécifié avec/F lorsque le traitement est terminé.|  
|/F|Utilisez un fichier réponse, tel que `odbcconf /F my.rsp`.<br /><br /> My. rsp peut se présenter comme suit :`REGSVR c:\my.dll`<br /><br /> /A n’est pas utilisé dans un fichier réponse.|  
|/H|Afficher l’utilisation (aide). Ce commutateur est le même que/ ?.|  
|/L [*mode*] *nom de fichier*|Envoyer la sortie du programme vers un fichier dans l’un des trois modes suivants : normal (n), verbose (v) et Debug (d). Le mode débogage enregistre les dll qui sont chargées par odbcconf. exe.<br /><br /> Si vous spécifiez/L sans mode, le fichier journal est vide.<br /><br /> Par exemple, **/LV log. txt**.|  
|/R|L’action sera effectuée après un redémarrage.|  
|/S|Mode silencieux. N’affiche pas les messages d’erreur.|  
  
 Les actions suivantes sont disponibles :  
  
|Action|Description|  
|------------|-----------------|  
|*Paramètres de configuration spécifiques au pilote CONFIGDRIVER DRIVER_NAME * **|Charge la DLL d’installation du pilote appropriée et appelle la fonction **ConfigDriver** .<br /><br /> Équivaut à la [fonction SQLConfigDriver](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Par exemple :<br /><br /> /A {CONFIGDRIVER "nom du pilote" "CPTimeout = 60"}<br /><br /> /A {CONFIGDRIVER "nom du pilote" "DriverODBCVer = 03.80"}|  
|CONFIGDSN *DRIVER_NAME* DSN =*nom* &#124; *attributs*|Ajoute ou modifie une source de données système.<br /><br /> Équivaut à la [fonction SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Par exemple :<br /><br /> /A {CONFIGDSN "SQL Server" "DSN = Name &#124; Server = SRV"}|  
|CONFIGSYSDSN *DRIVER_NAME* DSN =*nom* &#124; *attributs*|Ajoute ou modifie une source de données système.<br /><br /> Équivaut à la [fonction SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Par exemple :<br /><br /> /A {CONFIGSYSDSN "SQL Server" "DSN = Name &#124; Server = SRV"}|  
|INSTALLDRIVER|Équivalent à la [fonction SQLInstallDriverEx](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Pour plus d’informations sur la syntaxe de paires mot clé/valeur transmise à INSTALLDRIVER, consultez [sous-clés de spécification de pilote](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Par exemple :<br /><br /> /A {INSTALLDRIVER "Driver &#124; pilote = c:\your.dll &#124; Setup = c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; FileUsage = 0 &#124; SQLLevel = 1"}|  
|*Configuration du traducteur INSTALLTRANSLATOR * * chemin du pilote*|Ajoute des informations sur un traducteur au **HKEY_LOCAL_MACHINE \software\odbc\odbcinst. **Clé de Registre INI\ODBC Translators.<br /><br /> Équivalent à la [fonction SQLInstallTranslatorEx](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Pour plus d’informations sur la syntaxe de paires mot clé/valeur transmise à INSTALLDRIVER, consultez sous-clés de la [spécification du traducteur](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Par exemple :<br /><br /> /A {INSTALLTRANSLATOR "mon traducteur &#124; translateur = c:\My.dll &#124; Setup = c:\My.dll"}|  
|REGSVR, *dll*|Inscrit une DLL.<br /><br /> Équivalent à regsvr32. exe.<br /><br /> Par exemple :<br /><br /> /A {REGSVR c:\My.dll}|  
|SETFILEDSNDIR|Quand HKEY_LOCAL_MACHINE \SOFTWARE\ODBC\ODBC. Le fichier INI\ODBC DSN\DefaultDSNDir n’existe pas, l’action SETFILEDSNDIR le crée et lui attribue la valeur de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, ajoutée avec les sources \ODBC\Data.<br /><br /> Valeur à HKEY_LOCAL_MACHINE \SOFTWARE\ODBC\ODBC. INI\ODBC file DSN\DefaultDSNDir spécifie l’emplacement par défaut utilisé par l’administrateur de la source de données ODBC lors de la création d’une source de données basée sur des fichiers.<br /><br /> Par exemple :<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft ODBC (Open Database Connectivity)](../odbc/microsoft-open-database-connectivity-odbc.md)
