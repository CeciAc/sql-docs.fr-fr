---
title: AMO autres Classes et méthodes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- restores [AMO]
- AMO, backup and restore
- capture logs [AMO]
- AmoException class [AMO]
- Analysis Management Objects, backup and restore
- assembly objects [AMO]
- traces [AMO]
- backups [AMO]
ms.assetid: 60ed5cfa-3a03-4161-8271-0a71a3ae363b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 52148a4fb28988160858b7a74a7094797c1f0b34
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069809"
---
# <a name="amo-other-classes-and-methods"></a>Autres classes et méthodes AMO
  Cette section contient des classes courantes qui ne sont pas spécifiques à OLAP ou d’exploration de données, et qui sont utiles lors de l’administration ou la gestion des objets dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Ces classes recouvrent des fonctionnalités telles que les procédures stockées, le traçage, les exceptions, ainsi que la sauvegarde et la restauration.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Objets d’assembly](#Assembly)  
  
-   [Méthodes Backup et Restore](#Backup)  
  
-   [Objets de trace](#Traces)  
  
-   [Classe CaptureLog et attribut CaptureXML](#CaptureLog)  
  
-   [Classe d’Exception AMOException](#AMO)  
  
 L'illustration suivante montre la relation qui existe entre les classes décrites dans cette rubrique.  
  
 ![Autres Classes AMO](../../../analysis-services/dev-guide/media/amo-otherclasses.gif "autres Classes AMO")  
  
##  <a name="Assembly"></a>Objets d’assembly  
 Pour créer un objet <xref:Microsoft.AnalysisServices.Assembly>, il convient de l'ajouter à la collection d'assemblys du serveur, puis de mettre à jour l'objet <xref:Microsoft.AnalysisServices.Assembly> sur le serveur à l'aide de la méthode Update.  
  
 Pour supprimer un <xref:Microsoft.AnalysisServices.Assembly> de l’objet, il doit être supprimée à l’aide de la méthode Drop de le <xref:Microsoft.AnalysisServices.Assembly> objet. La suppression d'un objet <xref:Microsoft.AnalysisServices.Assembly> de la collection d'assemblys de la base de données n'a pas pour effet de supprimer l'assembly en question : elle ne fait que le masquer dans votre application jusqu'à la prochaine exécution de cette dernière.  
  
 Pour plus d’informations sur les méthodes et propriétés disponibles, consultez <xref:Microsoft.AnalysisServices.Assembly> dans <xref:Microsoft.AnalysisServices> .  
  
> [!IMPORTANT]  
>  Les assemblys COM peuvent présenter un risque pour la sécurité. En raison de ce risque et d'autres considérations, les assemblys COM ont été déconseillés dans [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]. Les assemblys COM peuvent ne pas être pris en charge dans les versions ultérieures.  
  
##  <a name="Backup"></a>Méthodes de sauvegarde et restauration  
 Backup et Restore sont des méthodes qui permettent de créer des copies d'une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et de récupérer cette dernière en utilisant ces copies. La méthode Backup appartient à l'objet <xref:Microsoft.AnalysisServices.Database>, tandis que la méthode Restore appartient à l'objet <xref:Microsoft.AnalysisServices.Server>.  
  
 Seuls les administrateurs de serveur et de base de données sont autorisés à procéder à la sauvegarde d'une base de données. Seuls les administrateurs de serveur peuvent restaurer une base de données sur un serveur différent de celui à partir duquel la sauvegarde a été effectuée. Les administrateurs de base de données ne peuvent restaurer une base de données en remplacement de la base de données existante que s'ils sont propriétaires de la base de données destinée à être remplacée. Après une restauration, l'administrateur de base de données peut perdre l'accès à la base de données restaurée si celle-ci est restaurée avec ses définitions de sécurité d'origine.  
  
 Les fichiers de sauvegarde de base de données doivent avoir une extension .abf.  
  
### <a name="backup-method"></a>Méthode Backup  
 Pour sauvegarder une base de données, utilisez la méthode Backup de l'objet de base de données en utilisant le nom du fichier de sauvegarde comme paramètre.  
  
##### <a name="default-values"></a>Valeurs par défaut :  
 AllowOverwrite=`false`  
  
 BackupRemotePartitions=`false`  
  
 Security=`CopyAll`  
  
 ApplyCompression=`true`  
  
### <a name="restore-method"></a>Méthode Restore  
 Pour restaurer une base de données sur un serveur, utilisez la méthode Restore du serveur en utilisant le nom du fichier de sauvegarde comme paramètre.  
  
##### <a name="default-values"></a>Valeurs par défaut :  
 AllowOverwrite=`false`  
  
 DataSourceType=`Remote`  
  
 Security=`CopyAll`  
  
##### <a name="restrictions"></a>Restrictions  
  
1.  Une partition locale ne peut pas être restaurée en tant que partition distante.  
  
2.  Une partition distante ne peut pas être restaurée en tant que partition locale, mais elle peut être restaurée sur un serveur différent de celui à partir duquel elle a été sauvegardée.  
  
### <a name="common-parameters-and-properties-for-backup-and-restore-methods"></a>Propriétés et paramètres communs aux méthodes Backup et Restore  
  
-   `File` est le nom du fichier de sauvegarde (nom UNC) cible/source.  
  
-   `Location` fournit des informations de sauvegarde spécifiques au serveur, telles que `BackupFile`. Vous pouvez ainsi spécifier un fichier de sauvegarde distinct pour une base de données distante.  
  
-   `DatasourceID` indique l'ID de la base de données subordonnée dans un serveur distant.  
  
-   `ConnectionString` vous permet d'ajuster la source de données distante dans le cas où le serveur distant a changé. DatasourceID doit toujours être spécifié quand ConnectionString est présent.  
  
-   `Folder` autorise le remappage des dossiers pour les partitions du disque dur local.  
  
-   `Original` est le dossier d'origine des partitions locales.  
  
-   `New` est le nouvel emplacement des partitions locales qui résidaient dans l'ancien dossier « Original » correspondant.  
  
-   S'il est spécifié, le paramètre `Password` indique que le serveur chiffrera le fichier de sauvegarde.  
  
##  <a name="Traces"></a>Objets de trace  
 Trace est une infrastructure destinée à surveiller, relire et gérer une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Une application cliente, comme [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], s'abonne à une trace et le serveur renvoie les événements de trace comme spécifié dans la définition de trace.  
  
 Chaque événement est décrit par une classe d'événements. La classe d'événements décrit le type d'événement généré. Au sein d'une classe d'événements, les sous-classes d'événements décrivent un niveau de catégorisation plus fin. Chaque événement est décrit par plusieurs colonnes. Les colonnes qui décrivent un événement de trace sont les mêmes pour tous les événements et sont conformes à la structure de Trace SQL. Les informations enregistrées dans chaque colonne peuvent varier en fonction de la classe d'événements ; autrement dit, un ensemble prédéfini de colonnes est défini pour chaque trace, mais la signification des colonnes peut être différente d'une classe d'événements à une autre. Par exemple, la colonne TextData sert à enregistrer les éléments ASSL d'origine pour tous les événements d'instruction.  
  
 Une définition de trace peut inclure une ou plusieurs classes d'événements à suivre simultanément. Pour chaque classe d'événements, une ou plusieurs colonnes de données peuvent être ajoutées à la définition de trace, mais il n'est pas obligatoire d'utiliser toutes les colonnes de trace. L'administrateur de base de données peut en effet choisir de n'inclure dans une trace qu'une partie des colonnes disponibles. En outre, les classes d'événements peuvent faire l'objet d'un suivi sélectif basé sur des critères de filtre appliqués à une colonne de trace.  
  
 Les traces peuvent être démarrées et supprimées. Plusieurs traces peuvent à tout moment être exécutées simultanément. Les événements de trace peuvent être capturés en temps réel ou dirigés vers un fichier pour une analyse ou une relecture ultérieure. [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] est l'outil utilisé pour analyser et relire les événements de trace [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Plusieurs connexions peuvent recevoir les événements d'une même trace.  
  
 Les traces peuvent être réparties en deux groupes : les traces de serveur et les traces de session. Les traces de serveur renseignent sur tous les événements du serveur ; les traces de session ne renseignent quant à elles que sur les événements de la session active.  
  
 Les traces issues de la collection de traces du serveur se définissent de la façon suivante :  
  
1.  Créez un objet <xref:Microsoft.AnalysisServices.Trace> et spécifiez ses données de base, notamment l'ID de trace, le nom, le nom du fichier journal, ajout|remplacement, etc.  
  
2.  Ajoutez les événements à surveiller à la collection d'événements de l'objet de trace. Pour chaque événement, des colonnes de données sont ajoutées.  
  
3.  Définissez des filtres pour exclure les lignes de données inutiles en les ajoutant à la collection de filtres.  
  
4.  Démarrez la trace ; la collecte de données ne démarre pas systématiquement une fois la trace créée.  
  
5.  Arrêtez la trace.  
  
6.  Examinez le fichier de trace avec [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)].  
  
 Les traces de l'objet de session sont obtenues de la façon suivante :  
  
1.  Définissez des fonctions pour gérer les événements de trace générés dans votre application par SessionTrace. Les événements possibles sont OnEvent et Stopped.  
  
2.  Ajoutez vos fonctions définies au gestionnaire d'événements.  
  
3.  Démarrez la trace de session.  
  
4.  Exécutez votre processus et laissez vos gestionnaires de fonction capturer les événements.  
  
5.  Arrêtez la trace de session.  
  
6.  Poursuivez avec votre application.  
  
##  <a name="CaptureLog"></a>Classe CaptureLog et attribut CaptureXML  
 Toutes les actions à exécuter par AMO sont envoyées au serveur sous forme de messages XMLA. AMO permet de capturer tous ces messages sans les en-têtes SOAP. Pour plus d’informations, consultez [présentation des Classes AMO](amo-classes-introduction.md). CaptureLog est le mécanisme d'AMO qui permet d'écrire sous forme de script les objets et les opérations ; les objets et les opérations sont écrits en XMLA.  
  
 Pour commencer à capturer les données XML, la propriété d'objet serveur CaptureXML doit être définie à `true`. Dès lors, toutes les actions qui doivent être envoyées au serveur commencent à être capturées dans la classe CaptureLog, sans que les actions soient envoyées au serveur. CaptureLog est considérée comme une classe, car elle possède une méthode, Clear, qui sert à effacer le journal de capture.  
  
 Pour lire le journal, vous devez obtenir la collection de chaînes et commencer à parcourir les chaînes. Vous pouvez également concaténer tous les journaux dans une chaîne en utilisant la méthode d'objet serveur ConcatenateCaptureLog. ConcatenateCaptureLog comprend trois paramètres dont deux sont obligatoires. Les paramètres requis sont *transactionnelle*, de type booléen, et *parallèles*, de type booléen. Si *transactionnelle* est défini sur `true`, il indique que le fichier de commandes XML sera créé comme une transaction unique au lieu de chaque commande est traitée comme une transaction distincte. Si *parallèles* est défini sur `true`, il indique que toutes les commandes dans le fichier de commandes seront enregistrées pour être exécutées simultanément et non séquentiellement comme ils ont été enregistrés.  
  
##  <a name="AMO"></a>Classe d’Exception AMOException  
 Vous pouvez utiliser la classe d'exception AMOException pour intercepter facilement les exceptions levées dans votre application par AMO.  
  
 AMO lève des exceptions lorsque certains problèmes sont rencontrés. Le tableau suivant répertorie les types d'exceptions gérés par AMO. Les exceptions sont dérivées de la classe <xref:Microsoft.AnalysisServices.AmoException>.  
  
|Exception|Origine|Description|  
|---------------|------------|-----------------|  
|<xref:Microsoft.AnalysisServices.AmoException>|Classe de base|L'application reçoit cette exception lorsqu'un objet parent obligatoire fait défaut ou qu'un élément demandé ne se trouve pas dans une collection.|  
|<xref:Microsoft.AnalysisServices.OutOfSyncException>|Dérivé d'AMOException|L'application reçoit cette exception quand AMO est désynchronisé avec le moteur et que celui-ci retourne une référence d'objet inconnue d'AMO.|  
|<xref:Microsoft.AnalysisServices.OperationException>|Dérivé d'AMOException|Exception importante souvent reçue par les applications. Cette exception contient les détails d'une erreur émanant du serveur, probablement en raison d'une opération AMO erronée comme Update, Process ou Drop.|  
|<xref:Microsoft.AnalysisServices.ResponseFormatException>|Dérivé d'AMOException|Cette exception se produit lorsque le moteur retourne un message dans un format illisible pour AMO.|  
|<xref:Microsoft.AnalysisServices.ConnectionException>|Dérivé d'AMOException|Cette exception se produit lorsqu'il est impossible d'établir une connexion (avec Server.Connect) ou que la connexion se perd pendant qu'AMO communique avec le moteur (par exemple, pendant une opération Update, Process ou Drop).|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices>   
 [Présentation des Classes AMO](amo-classes-introduction.md)   
 [Architecture logique &#40;Analysis Services - données multidimensionnelles&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Objets de base de données &#40;Analysis Services - données multidimensionnelles&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
