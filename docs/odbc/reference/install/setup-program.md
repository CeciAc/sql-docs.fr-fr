---
title: Programme d’installation | Microsoft Docs
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc79bb5d12b53938e3e2ef1c531fd03b0002ed78
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093833"
---
# <a name="setup-program"></a>Programme d’installation
> **REMARQUE :** À partir de Windows XP et Windows Server 2003, **ODBC est inclus dans le système d’exploitation Windows**. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 L’utilisateur exécute le programme d’installation pour démarrer le processus d’installation. Le programme d’installation est écrit par le développeur de l’application ou le pilote. Outre l’installation des composants ODBC, il peut installer d’autres logiciels. Par exemple, les développeurs d’applications peuvent utiliser le même programme d’installation pour installer les composants ODBC et d’installer leurs applications.  
  
 Les développeurs peuvent écrire à partir de zéro, le programme d’installation à l’aide des utilitaires d’installation de kit de développement logiciel Microsoft® Windows® ou de logiciel d’installation à partir d’autres fournisseurs. Ainsi, les développeurs qui contrôle total sur l’apparence du programme d’installation. Le programme d’installation peut être écrits pour installer des logiciels supplémentaires, comme une application ODBC. Pour plus d’informations sur les utilitaires du programme d’installation du Kit de développement logiciel Windows, consultez la documentation du SDK Windows.  
  
 La quantité de l’installation s’effectue par le programme d’installation dépend de ce que les appels dans le programme d’installation DLL de fonctions. Le programme d’installation DLL contient des fonctions pour installer des composants ODBC individuels. Le programme d’installation appelle simplement **SQLInstallDriverManager**, **SQLInstallDriverEx**, ou **SQLInstallTranslatorEx** dans le programme d’installation DLL pour récupérer le chemin d’accès de la répertoire dans lequel le composant à installer et d’ajouter des informations sur le composant dans le Registre. Ces fonctions ne copient pas réellement les fichiers ; le programme d’installation utilise pour cela les informations dans les arguments de ces fonctions.  
  
 Le programme d’installation DLL contient également des fonctions pour supprimer des composants ODBC. Le programme d’installation appelle **SQLRemoveDriverManager**, **SQLRemoveDriver**, ou **SQLRemoveTranslator** nombre de DLL pour diminuer l’utilisation d’un composant dans le programme d’installation dans le Registre et, si le décompte d’utilisation du composant nouveau tombe à 0, supprimez toutes les informations sur le composant à partir du Registre. Ces fonctions ne suppriment pas réellement les fichiers pour le composant ; le programme d’installation pour cela, si le décompte d’utilisation tombe à 0.
