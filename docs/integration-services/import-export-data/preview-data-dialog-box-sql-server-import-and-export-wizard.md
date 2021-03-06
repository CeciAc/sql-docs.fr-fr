---
title: Boîte de dialogue Aperçu des données (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: feeef370bc64697e3fa9ef3a279e31ba047301fd
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296318"
---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a>Boîte de dialogue Aperçu des données (Assistant Importation et Exportation SQL Server)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Après avoir spécifié les données à copier, vous pouvez éventuellement cliquer sur **Aperçu** pour ouvrir la boîte de dialogue **Aperçu des données** . Dans cette page, vous pouvez afficher jusqu’à 200 lignes d’exemples de données de votre source de données. Cela confirme que l’Assistant va copier les données que vous souhaitez copier.
  
## <a name="screen-shot-of-the-preview-data-page"></a>Capture d’écran de la page Aperçu des données 
 La capture d’écran suivante montre la boîte de dialogue **Aperçu des données** de l’Assistant.  
 
![Page Aperçu des données de l’Assistant Importation et Exportation](../../integration-services/import-export-data/media/preview-data.png "Page Aperçu des données de l’Assistant Importation et Exportation")  
  
## <a name="preview-sample-data"></a>Aperçu des exemples de données  
 **Source**  
Affiche la requête que l’Assistant utilise pour charger des données à partir de la source de données.

Si vous avez sélectionné une table à copier, le champ **Source** affiche une requête `SELECT * FROM <table>` au lieu du nom de la table. 
  
 **Exemple de grille de données**  
 Affiche jusqu’à 200 lignes d’exemples de données retournées par la requête à partir de la source de données.  


## <a name="thats-not-right-i-want-to-change-something"></a>Ce n’est pas bon, je souhaite modifier quelque chose
Après avoir affiché un aperçu des données, vous souhaiterez peut-être modifier les options que vous avez sélectionnées dans les pages précédentes de l’Assistant. Pour effectuer ces modifications, cliquez sur **OK** pour revenir à la page **Sélectionner les tables et les vues sources**, puis cliquez sur **Précédent** pour revenir aux pages précédentes où vous pouvez modifier vos sélections.

## <a name="whats-next"></a>Quelle est l’étape suivante ?  
 Une fois que vous avez affiché un aperçu des données à copier et cliqué sur **OK**, la boîte de dialogue **Aperçu des données** vous renvoie à la page **Sélectionner les tables et les vues sources** ou **Configurer la destination du fichier plat** . Pour plus d’informations, consultez [Sélectionner les tables et les vues sources](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) ou [Configurer la destination du fichier plat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Voir aussi
[Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)
