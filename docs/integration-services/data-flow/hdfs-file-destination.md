---
title: Destination du fichier HDFS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 88b6bc5bafcc2fe3da77b55ac98d19ab7ec747e2
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35410701"
---
# <a name="hdfs-file-destination"></a>HDFS File Destination
  Le composant HDFS File Destination permet à un package SSIS d’écrire des données dans un fichier HDFS. Les formats de fichier pris en charge sont les formats texte, Avro et ORC.  
  
 Pour configurer HDFS File Destination, opérez un glisser-déplacer de HDFS File Source vers le concepteur de flux de données, puis double-cliquez sur le composant pour ouvrir l’éditeur.  
  
 ![Éditeur de la destination du fichier HDFS](../../integration-services/data-flow/media/hdfs-file-dest.png "Éditeur de la destination du fichier HDFS")  
  
## <a name="options"></a>Options  
 Configurez les options suivantes sur l’onglet **General (Général)** de la boîte de dialogue **Hadoop File Destination Editor (Éditeur de destination de fichiers Hadoop)** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où se trouvent les fichiers HDFS.|  
|**Chemin d'accès au fichier**|Spécifiez le nom du fichier HDFS.|  
|**Format du fichier**|Spécifiez le format du fichier HDFS. Les options disponibles sont Texte, Avro et ORC.|  
|**Caractère séparateur de colonnes**|Si vous avez sélectionné le format Texte, spécifiez le caractère délimiteur de colonne.|  
|**Noms de colonnes dans la première ligne de données**|Si vous avez sélectionné le format Texte, indiquez si la première ligne du fichier contient les noms de colonnes.|  
  
 Après avoir configuré ces options, sélectionnez l’onglet **Colonnes** pour mapper les colonnes source aux colonnes de destination dans le flux de données.  
  
## <a name="see-also"></a> Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Source de fichier HDFS](../../integration-services/data-flow/hdfs-file-source.md)  
  
  
