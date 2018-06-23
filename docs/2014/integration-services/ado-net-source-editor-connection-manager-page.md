---
title: Éditeur de Source ADO NET (Page Gestionnaire de connexions) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9ef6c300f4954d776dc3ca6bbb5a0504c56b0c3d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052902"
---
# <a name="ado-net-source-editor-connection-manager-page"></a>Éditeur de source ADO NET (page Gestionnaire de connexions)
  La page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source ADO NET** permet de sélectionner le gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] pour la source. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
 Pour en savoir plus sur la source ADO NET, consultez [ADO NET Source](data-flow/ado-net-source.md).  
  
 **Pour ouvrir la page Gestionnaire de connexions**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui possède la source ADO NET.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source ADO NET.  
  
3.  Dans **l’Éditeur de source ADO NET**, cliquez sur **Gestionnaire de connexions**.  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions ADO.NET**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à partir de la boîte de dialogue **Configurer le gestionnaire de connexions ADO.NET** .  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Table ou vue|Permet de récupérer les données d’une table ou d’une vue dans la source de données [!INCLUDE[vstecado](../includes/vstecado-md.md)] .|  
|Commande SQL|Permet de récupérer les données auprès de la source de données [!INCLUDE[vstecado](../includes/vstecado-md.md)] à l’aide d’une requête SQL.|  
  
 **Aperçu**  
 Affichez un aperçu des résultats à partir de la boîte de dialogue **Vue de données** . Le mode**Aperçu** peut afficher jusqu’à 200 lignes.  
  
> [!NOTE]  
>  Lorsque vous affichez l'aperçu des données, les colonnes ayant un type CLR défini par l'utilisateur ne contiennent pas de données. Les valeurs \<valeur trop grande pour être affichée> ou System.Byte[] s’affichent à la place. La première s'affiche lorsque le fournisseur [!INCLUDE[vstecado](../includes/vstecado-md.md)] accède à la source de données ; la seconde lorsque vous utilisez le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
  
### <a name="data-access-mode--table-or-view"></a>Mode d'accès aux données = Table ou vue  
 **Nom de la table ou de la vue**  
 Sélectionnez le nom de la table ou de la vue dans la liste de celles qui sont disponibles dans la source de données.  
  
### <a name="data-access-mode--sql-command"></a>Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d’une requête SQL, générez la requête en cliquant sur **Générer une requête**ou recherchez le fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
 **Construire une requête**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , localisez le fichier qui contient le texte de la requête SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source ADO NET &#40;Page colonnes&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [Éditeur de Source ADO NET &#40;Page sortie d’erreur&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md)   
 [Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md)  
  
  