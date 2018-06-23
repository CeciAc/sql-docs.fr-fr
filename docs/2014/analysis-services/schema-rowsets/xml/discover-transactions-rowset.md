---
title: Ensemble de lignes DISCOVER_TRANSACTIONS | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3869d4f8cd3adf96bd006a8669d7d82778b02450
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040530"
---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS, ensemble de lignes
  Retourne l'ensemble actuel des transactions en attente sur le système.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_TRANSACTIONS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Description|  
|-----------------|--------------------|-----------------|  
|`TRANSACTION_ID`|`DBTYPE_WSTR`|Identificateur unique de la transaction, tel qu'un GUID.|  
|`TRANSACTION_SESSION_ID`|`DBTYPE_WSTR`|Identificateur unique de la session de transaction, tel qu'un GUID.|  
|`TRANSACTION_START_TIME`|`DBTYPE_DBTIMESTAMP`|Date et heure UTC du serveur auxquelles la transaction a démarrée.|  
|`TRANSACTION_ELAPSED_TIME_MS`|`DBTYPE_I8`|Durée écoulée, en millisecondes, depuis le début de l'exécution de la transaction.|  
|`TRANSACTION_CPU_TIME_MS`|`DBTYPE_I8`|Temps processeur, en millisecondes, consommé par toutes les requêtes depuis le début de la transaction.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_TRANSACTIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|**Nom de colonne**|**Indicateur de type**|**État de la restriction**|  
|---------------------|------------------------|---------------------------|  
|`ID`|`DBTYPE_WSTR`|Facultatif.|  
|`SESSION_ID`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  