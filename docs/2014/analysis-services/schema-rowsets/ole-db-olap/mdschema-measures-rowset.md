---
title: Ensemble de lignes MDSCHEMA_MEASURES | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_MEASURES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6608c64caa882499282ad7a7e30090ab4118b522
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038189"
---
# <a name="mdschemameasures-rowset"></a>Ensemble de lignes MDSCHEMA_MEASURES
  Décrit chaque mesure dans un cube.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_MEASURES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom du catalogue auquel appartient cette mesure. Valeur `NULL` si le fournisseur ne prend pas en charge les catalogues.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nom du schéma auquel appartient cette mesure. `NULL` si le fournisseur ne prend pas en charge les schémas.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube auquel appartient cette mesure.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`||Nom de la mesure.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la mesure. Pour les fournisseurs qui produisent des noms uniques par qualification, chaque composant du nom est délimité.|  
|`MEASURE_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée à la mesure. Principalement utilisée à des fins d'affichage. Si une légende n’existe pas, `MEASURE_NAME` est retourné.|  
|`MEASURE_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`MEASURE_AGGREGATOR`|`DBTYPE_I4`||Énumération qui indique comment une mesure a été dérivée. Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   `MDMEASURE_AGGR_SUM` (`1`) identifie que la mesure agrège à partir de `SUM`.<br />-   `MDMEASURE_AGGR_COUNT` (`2`) identifie que la mesure agrège à partir de `COUNT`.<br />-   **MDMEASURE_AGGR_MIN** (`3`) identifie que la mesure agrège à partir de `MIN`.<br />-   **MDMEASURE_AGGR_MAX** (`4`) identifie que la mesure agrège à partir de `MAX`.<br />-   `MDMEASURE_AGGR_AVG` (`5`) identifie que la mesure agrège à partir de `AVG`.<br />-   `MDMEASURE_AGGR_VAR` (`6`) identifie que la mesure agrège à partir de `VAR`.<br />-   `MDMEASURE_AGGR_STD` (`7`) identifie que la mesure agrège à partir de `STDEV`.<br />-   `MDMEASURE_AGGR_DST` (`8`) identifie que la mesure agrège à partir de `DISTINCT COUNT`.<br />-   `MDMEASURE_AGGR_NONE` (`9`) identifie que la mesure agrège à partir de `NONE`.<br />-   `MDMEASURE_AGGR_AVGCHILDREN` (`10`) identifie que la mesure agrège à partir de `AVERAGEOFCHILDREN`.<br />-   `MDMEASURE_AGGR_FIRSTCHILD` (`11`) identifie que la mesure agrège à partir de `FIRSTCHILD`.<br />-   `MDMEASURE_AGGR_LASTCHILD` (`12`) identifie que la mesure agrège à partir de `LASTCHILD`.<br />-   `MDMEASURE_AGGR_FIRSTNONEMPTY` (`13`) identifie que la mesure agrège à partir de `FIRSTNONEMPTY`,<br />-   `MDMEASURE_AGGR_LASTNONEMPTY` (`14`) identifie que la mesure agrège à partir de `LASTNONEMPTY`.<br />-   `MDMEASURE_AGGR_BYACCOUNT` (`15`) identifie que la mesure agrège à partir de `BYACCOUNT`.<br />-   `MDMEASURE_AGGR_CALCULATED` (`127`) indique que la mesure a été dérivée à partir d’une formule qui n’était pas celles citées ci-dessus.<br />-   `MDMEASURE_AGGR_UNKNOWN` (`0`) indique que la mesure a été dérivée à partir d’une fonction d’agrégation inconnue ou de la formule.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Type de données de la mesure.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Précision maximale de la propriété si le type de données de l'objet de mesure est une valeur numérique exacte. `NULL` pour tous les autres types de propriété.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Nombre de chiffres situés à droite de la virgule décimale si l'indicateur de type de l'objet de mesure est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`. Sinon, cette valeur est `NULL`.|  
|`MEASURE_UNITS`|`DBTYPE_WSTR`||Non pris en charge|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description explicite de la mesure. `NULL` si aucune description n'existe.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Une expression pour le membre.|  
|`MEASURE_IS_VISIBLE`|`DBTYPE_BOOL`||Valeur booléenne qui retourne toujours True. Si la mesure n'est pas visible, elle n'est pas incluse dans l'ensemble de lignes du schéma.|  
|`LEVELS_LIST`|`DBTYPE_WSTR`||Chaîne qui retourne toujours `NULL`.|  
|`MEASURE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Nom de la colonne de la requête SQL qui correspond au nom de la mesure.|  
|`MEASURE_UNQUALIFIED_CAPTION`|`DBTYPE_WSTR`||Nom de la mesure, non qualifié avec le nom du groupe de mesures.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Nom du groupe de mesures auquel appartient cette mesure.|  
|`MEASURE_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Chemin d'accès à utiliser pour l'affichage de la mesure dans l'interface utilisateur. Les noms de dossiers doivent être séparés par un point-virgule. Les dossiers imbriqués sont indiqués par une barre oblique inverse (\\).|  
|`DEFAULT_FORMAT_STRING`|`DBTYPE_WSTR`||Chaîne de format par défaut pour la mesure.|  
  
 L'ensemble de lignes est trié sur `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASURE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_MEASURES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
|`MEASURE_VISIBILITY`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -1 Visible<br />-2 n’est pas Visible<br /><br /> La restriction par défaut est la valeur 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  