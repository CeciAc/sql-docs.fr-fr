---
title: Créer des rapports d’analyse
description: Créer des rapports d’analyse dans Assistant Expérimentation de base de données
ms.date: 11/21/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 4d3f057ffcfb1030b473b69f96b7204b3a975613
ms.sourcegitcommit: aaa42f26c68abc2de10eb58444fe6b490c174eab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74307972"
---
# <a name="create-analysis-reports-in-database-experimentation-assistant-sql-server"></a>Créer des rapports d’analyse en Assistant Expérimentation de base de données (SQL Server)

Une fois que vous avez relu le suivi source sur les deux serveurs cibles, vous pouvez générer un rapport d’analyse en Assistant Expérimentation de base de données (DEA). Les rapports d’analyse vous aident à obtenir des informations sur les implications sur les performances des modifications proposées.

## <a name="create-an-analysis-report"></a>Créer un rapport d’analyse

Dans DEA, sélectionnez l’icône de menu. Dans le menu développé, sélectionnez **rapports d’analyse** en regard de l’icône de liste de vérification.

![Menu analyse](./media/database-experimentation-assistant-create-report/dea-create-reports-menu.png)

Sous **rapports d’analyse**, sélectionnez **nouveau rapport d’analyse**.

![Menu nouveau rapport d’analyse](./media/database-experimentation-assistant-create-report/dea-create-reports-new-report.png)

Entrez ou sélectionnez les informations suivantes :

- **Nom du rapport**: entrez un nom pour votre rapport. Le nom du rapport est utilisé à la fois pour les bases de données A et B. Exemple :*identificateur unique*d’un*nom* +  *de rapport (ou B)* + .
- **Nom du serveur**: entrez le nom de l’ordinateur serveur que vous souhaitez inclure dans les bases de données d’analyse, B et.
- **SQL Server nom**de l’instance : entrez le nom de l’instance de SQL Server à utiliser pour le rapport.
- **Trace pour le serveur source**: entrez le premier fichier de trace (. trc) SQL Server (2008 R2).
- **Trace pour le serveur cible**: entrez le fichier SQL Server cible (2014) First. trc.

![Page nouveau rapport d’analyse](./media/database-experimentation-assistant-create-report/dea-create-reports-inputs.png)

## <a name="generate-a-report"></a>Générer un rapport

Une fois que vous avez entré ou sélectionné les informations requises dans la page **nouveau rapport d’analyse** , sélectionnez **Démarrer** pour commencer à créer le rapport. Si les informations que vous avez entrées sont valides, le rapport d’analyse est créé. Dans le cas contraire, les zones de texte qui contiennent des informations non valides sont mises en surbrillance en rouge. Veillez à entrer les valeurs correctes, puis sélectionnez **Démarrer**.

Un nouveau rapport d’analyse est généré. La base de données d’analyse suit l’identification du schéma d’appellation + + *identificateur unique*du *nom de rapport spécifié par l’utilisateur*.

## <a name="frequently-asked-questions-about-analysis-reports"></a>Forum aux questions sur les rapports d’analyse

**Q : qu’est-ce que mon rapport d’analyse me dit ?**

La DEA utilise des tests statistiques pour analyser votre charge de travail et déterminer le mode d’exécution de chaque requête de la cible 1 à la cible 2. Il fournit des détails sur les performances de chaque requête. Pour en savoir plus sur la DEA, [consultez prise en main](database-experimentation-assistant-get-started.md).

**Q : puis-je créer un rapport d’analyse lors de la génération d’un autre rapport ?**

Non.  Actuellement, un seul rapport peut être généré à la fois pour éviter les conflits. Toutefois, vous pouvez exécuter plusieurs captures et relire en même temps.

**Q : J’ai mis à niveau la DEA vers la version 2,0. Puis-je toujours afficher et utiliser mes anciens rapports ?**

Oui. Pour afficher les rapports précédemment générés, vous devez mettre à jour le schéma du rapport. Pour plus d’informations, 2,0 consultez la page relative [à la mise à jour du schéma de base de données pour l’analyse de DEA](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-updating-db-schema-for-analysis-report-in-the-database-experimentation-assistant/).

**Q : puis-je générer un rapport d’analyse à l’aide de l’invite de commandes ?**

Oui. Vous pouvez générer un rapport d’analyse à partir de l’invite de commandes. Vous pouvez ensuite afficher le rapport dans l’interface utilisateur. Pour plus d’informations, consultez [exécuter à l’invite de commandes](database-experimentation-assistant-run-command-prompt.md).

## <a name="troubleshoot-analysis-reports"></a>Dépanner les rapports d’analyse

**Q : Quelles sont les autorisations de sécurité nécessaires pour générer et afficher un rapport d’analyse sur mon serveur ?**

L’utilisateur qui est connecté à DEA doit disposer de droits d’administrateur système sur le serveur d’analyse. Si l’utilisateur fait partie d’un groupe, assurez-vous que le groupe dispose des droits d’administrateur système.

|Erreurs possibles|Solution|  
|---|---|  
|Impossible de se connecter à la base de données. Vérifiez que vous disposez des droits d’administrateur système pour l’analyse et l’affichage des rapports.|Vous ne disposez peut-être pas d’un accès ou de droits d’administrateur système sur le serveur ou la base de données. Confirmez vos droits de connexion, puis réessayez.|  
|Impossible de générer le **nom du rapport** sur le nom du **serveur**serveur. Pour plus d’informations, consultez le rapport **nom du rapport** .|Vous ne disposez peut-être pas des droits d’administrateur système nécessaires pour générer un nouveau rapport. Pour afficher les erreurs détaillées, sélectionnez le rapport d’erreur et vérifiez les journaux dans% Temp%\\DEA.|  
|L’utilisateur actuel ne dispose pas des autorisations requises pour exécuter l’opération. Vérifiez que vous disposez des droits d’administrateur système pour effectuer la trace et analyser les rapports.|Vous ne disposez pas des droits sysadmin nécessaires pour générer un nouveau rapport.|  

**Q : je ne peux pas me connecter à l’ordinateur exécutant SQL Server**

- Confirmez que le nom de l’ordinateur exécutant SQL Server est valide. Pour confirmer, essayez de vous connecter au serveur à l’aide de SQL Server Management Studio (SSMS).
- Vérifiez que la configuration de votre pare-feu ne bloque pas les connexions à l’ordinateur exécutant SQL Server.
- Confirmez que l’utilisateur dispose des droits d’utilisateur requis.

Vous pouvez obtenir plus de détails dans les journaux de% temp\\% DEA. Si le problème persiste, contactez l’équipe du produit.

**Q : une erreur s’affiche lors de la génération d’un rapport d’analyse**

L’accès à Internet est nécessaire la première fois que vous générez un rapport d’analyse après l’installation de DEA. L’accès à Internet est nécessaire pour télécharger les packages requis pour l’analyse statistique.

Si une erreur se produit pendant la création du rapport, la page progression affiche l’étape spécifique à laquelle la génération de l’analyse a échoué. Vous pouvez obtenir plus de détails dans les journaux de% temp\\% DEA. Vérifiez que vous disposez d’une connexion valide au serveur avec les droits d’utilisateur requis, puis réessayez. Si le problème persiste, contactez l’équipe du produit.

|Erreurs possibles|Solution|  
|---|---|  
|RInterop a rencontré une erreur au démarrage. Vérifiez les journaux RInterop et réessayez.|La DEA requiert un accès à Internet pour télécharger les packages R dépendants. Vérifiez les journaux RInterop dans% Temp\\% RInterop et les journaux de DEA dans\\% Temp% DEA. Si RInterop a été initialisé de manière incorrecte ou s’il a été initialisé sans les packages R corrects, vous pouvez voir l’exception « échec de la génération d’un nouveau rapport d’analyse » après l’étape InitializeRInterop dans les journaux de DEA.<br><br>Les journaux RInterop peuvent également afficher une erreur semblable à « aucun package jsonlite n’est disponible ». Si votre ordinateur n’a pas accès à Internet, vous pouvez télécharger manuellement le package jsonlite R requis :<br><br><li>Accédez au dossier% UserProfile%\\DEARPackages sur le système de fichiers de l’ordinateur. Ce dossier est constitué des packages utilisés par R pour DEA.</li><br><li>Si le dossier jsonlite est manquant dans la liste des packages installés, vous devez disposer d’un ordinateur disposant d’un accès à Internet pour\_Télécharger la version finale [https://cran.r-project.org/web/packages/jsonlite/index.html](https://cran.r-project.org/web/packages/jsonlite/index.html)de jsonlite 1.4. zip à partir de.</li><br><li>Copiez le fichier. zip sur l’ordinateur sur lequel vous exécutez la DEA.  Extrayez le dossier jsonlite et copiez-le\\dans% UserProfile% DEARPackages. Cette étape installe automatiquement le package jsonlite dans R. Le dossier doit être nommé **jsonlite** et le contenu doit se trouver directement à l’intérieur du dossier, et non un niveau ci-dessous.</li><br><li>Fermez la DEA, rouvrez, puis réessayez l’analyse.</li><br>Vous pouvez également utiliser l’RGUI. Accédez à **packages** > **installation à partir de zip**. Accédez au package que vous avez téléchargé précédemment et installez.<br><br>Si RInterop a été initialisé et configuré correctement, vous devez voir « Installation du package R dépendant jsonlite » dans les journaux RInterop.|  
|Impossible de se connecter à l’instance de SQL Server, assurez-vous que le nom du serveur est correct et vérifiez l’accès requis pour l’utilisateur qui est connecté.|Vous ne disposez peut-être pas d’un accès ou de droits d’utilisateur sur le serveur, ou le nom du serveur est peut-être incorrect.|
|Délai d’attente du processus RInterop dépassé. Vérifiez les journaux de DEA et RInterop, arrêtez le processus RInterop dans le gestionnaire des tâches, puis réessayez.<br><br>ou<br><br>RInterop est en état d’erreur. Arrêtez le processus RInterop dans le gestionnaire des tâches, puis réessayez.|Vérifiez les journaux dans% Temp\\% RInterop pour confirmer l’erreur. Supprimez le processus RInterop du gestionnaire des tâches avant de réessayer. Si le problème persiste, contactez l’équipe du produit.|

**Q : le rapport est généré, mais les données semblent manquer**

Vérifiez la base de données sur l’ordinateur d’analyse qui exécute SQL Server pour vérifier que les données existent. Vérifiez que la base de données d’analyse existe et vérifiez ses tables. Par exemple, vérifiez les tables suivantes : TblBatchesA, TblBatchesB et TblSummaryStats.

Si les données n’existent pas, les données risquent de ne pas avoir été copiées correctement ou la base de données est peut-être endommagée. Si seules certaines données sont manquantes, les fichiers de trace créés lors de la capture ou de la relecture n’ont peut-être pas été capturés correctement dans votre charge de travail. Si les données sont présentes, vérifiez les fichiers journaux dans% Temp%\\DEA pour voir si des erreurs ont été consignées. Ensuite, réessayez de générer le rapport d’analyse.

Vous avez d’autres questions ou des commentaires ? Envoyez vos commentaires par le biais de l’outil DEA en choisissant l’icône représentant un smiley dans le coin inférieur gauche. 

## <a name="see-also"></a>Voir aussi

- Pour savoir comment afficher le rapport d’analyse, consultez [afficher les rapports](database-experimentation-assistant-view-report.md).
