---
title: Ensemble de lignes de schéma DBSCHEMA_PROVIDER_TYPES | Microsoft Docs
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
- DBSCHEMA_PROVIDER_TYPES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bca2527b77df65dede59878e91ef88ec5f933e0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250949"
---
# <a name="dbschemaprovidertypes-rowset"></a>Ensemble de lignes de schéma DBSCHEMA_PROVIDER_TYPES
  Identifie les types de données (de base) pris en charge par le fournisseur de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DBSCHEMA_PROVIDER_TYPES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TYPE_NAME`|`DBTYPE_WSTR`||Nom du type de données spécifique au fournisseur.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicateur du type de données.|  
|`COLUMN_SIZE`|`DBTYPE_UI4`||Longueur d'un paramètre ou d'une colonne non numérique qui fait référence soit à la longueur maximale soit à la longueur définie pour ce type par le fournisseur. Pour les données de type caractère, il s'agit de la longueur maximale ou de la longueur définie en nombre de caractères. Pour les données de type DateTime, il s'agit de la longueur de la représentation de chaîne (en supposant la précision maximale autorisée pour le composant fractions de secondes).<br /><br /> Si les données sont de type numérique, il s'agit de la limite supérieure de la précision maximale du type de données.|  
|`LITERAL_PREFIX`|`DBTYPE_WSTR`||Caractère(s) utilisé(s) comme préfixe pour un littéral de ce type dans une commande de texte.|  
|`LITERAL_SUFFIX`|`DBTYPE_WSTR`||Caractère(s) utilisé(s) comme suffixe pour un littéral de ce type dans une commande de texte.|  
|`CREATE_PARAMS`|`DBTYPE_WSTR`||Paramètres de création spécifiés par l'utilisateur lors de la création d'une colonne de ce type de données. Par exemple, le type de données SQL, `DECIMAL,` requiert une précision et une échelle. Dans ce cas, les paramètres de création peuvent être la chaîne "précision, échelle". Dans une commande de texte pour créer une colonne `DECIMAL` avec une précision de 10 et une échelle de 2, la valeur de la colonne `TYPE_NAME` pourrait être `DECIMAL()` et la spécification de type complète serait `DECIMAL(10,2)`.<br /><br /> Les paramètres de création apparaissent sous la forme d'une liste de valeurs séparées par des virgules, dans l'ordre où elles sont fournies et sans parenthèses. Si un paramètre de création est longueur, longueur maximale, précision, échelle, valeur de départ ou incrément, utilisez "length", "max length", "precision", "scale", "seed" et "increment", respectivement. Si le paramètre de création est une autre valeur, le fournisseur détermine quel texte sera utilisé pour décrire le paramètre de création.<br /><br /> Si le type de données requiert des paramètres de création, "()" apparaît généralement dans le nom de type. Cela indique la position à laquelle insérer les paramètres de création. Si le nom de type n'inclut pas "()", les paramètres de création sont placés entre parenthèses et ajoutés au nom du type de données.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données autorise la valeur Null.<br /><br /> `VARIANT_TRUE` indique que le type de données autorise la valeur Null.<br /><br /> `VARIANT_FALSE` Indique que le type de données n’est pas nullable.<br /><br /> `NULL` indique que le fait que le type de données autorise ou non la valeur Null n'est pas connu.|  
|`CASE_SENSITIVE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données est de type caractère et s'il respecte la casse.<br /><br /> `VARIANT_TRUE` indique que les données sont de type caractère et qu'elles respectent la casse.<br /><br /> `VARIANT_FALSE` indique que les données ne sont pas de type caractère ou qu'elles ne respectent pas la casse.|  
|`SEARCHABLE`|`DBTYPE_UI4`||Entier qui indique comment le type de données peut être utilisé dans les recherches si le fournisseur prend en charge `ICommandText` ; sinon, `NULL`.<br /><br /> Les valeurs possibles pour cette colonne sont les suivantes :<br /><br /> -   `DB_UNSEARCHABLE` Indique que le type de données ne peut pas être utilisé dans un `WHERE` clause.<br />-   `DB_LIKE_ONLY` Indique que le type de données peut être utilisé dans un `WHERE` clause uniquement avec le `LIKE` prédicat.<br />-   `DB_ALL_EXCEPT_LIKE` Indique que le type de données peut être utilisé dans un `WHERE` clause avec tous les opérateurs de comparaison à l’exception `LIKE`.<br />-   `DB_SEARCHABLE` Indique que le type de données peut être utilisé dans un `WHERE` clause avec n’importe quel opérateur de comparaison.|  
|`UNSIGNED_ATTRIBUTE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données est non signé.<br /><br /> `VARIANT_TRUE` indique que le type de données est non signé.<br /><br /> `VARIANT_FALSE` indique que le type de données est signé.<br /><br /> `NULL` indique que ce paramètre n'est pas applicable à ce type de données.|  
|`FIXED_PREC_SCALE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données a une précision fixe et une échelle.<br /><br /> `VARIANT_TRUE` indique que le type de données a une précision fixe et une échelle.<br /><br /> `VARIANT_FALSE` indique que le type de données n'a pas une précision fixe et une échelle.|  
|`AUTO_UNIQUE_VALUE`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données est à auto-incrémentation.<br /><br /> `VARIANT_TRUE` indique que les valeurs de ce type peuvent être incrémentées automatiquement.<br /><br /> `VARIANT_FALSE` indique que les valeurs de ce type ne peuvent pas être incrémentées automatiquement.<br /><br /> Si cette valeur est `VARIANT_TRUE`, le fait qu'une colonne de ce type soit toujours incrémentée automatiquement dépend de la propriété de colonne `DBPROP_COL_AUTOINCREMENT` du fournisseur. Si la propriété `DBPROP_COL_AUTOINCREMENT` est en lecture/écriture, le fait qu'une colonne de ce type soit ou non incrémentée automatiquement dépend du paramètre de la propriété `DBPROP_COL_AUTOINCREMENT`. Si `DBPROP_COL_AUTOINCREMENT` est une propriété en lecture seule, soit la totalité soit aucune des colonnes de ce type ne seront incrémentées automatiquement.|  
|`LOCAL_TYPE_NAME`|`DBTYPE_WSTR`||La version localisée de `TYPE_NAME`. `NULL`est retournée si un nom localisé n'est pas pris en charge par le fournisseur de données.|  
|`MINIMUM_SCALE`|`DBTYPE_I2`||Si l'indicateur de type est `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL` ou `DBTYPE_NUMERIC`, nombre minimal de chiffres autorisés à droite de la virgule décimale. Sinon, `NULL`.|  
|`MAXIMUM_SCALE`|`DBTYPE_I2`||Nombre maximal de chiffres autorisés à droite de la virgule décimale si l'indicateur de type est `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL` ou `DBTYPE_NUMERIC` ; sinon, N`U`LL.|  
|`GUID`|`DBTYPE_GUID`||(Destiné à une utilisation ultérieure) `GUID` du type, si le type est décrit dans une bibliothèque de types. Sinon, `NULL`.|  
|`TYPELIB`|`DBTYPE_WSTR`||(Destiné à une utilisation ultérieure) Bibliothèque de types contenant la description du type, s'il est décrit dans une bibliothèque de types. Sinon, NULL.|  
|`VERSION`|`DBTYPE_WSTR`||(Destiné à une utilisation ultérieure) Version de la définition du type. Les fournisseurs peuvent attribuer des versions aux définitions de type. Des fournisseurs différents peuvent utiliser des méthodes de suivi des versions différentes, par exemple un horodateur ou un nombre (entier ou flottant). `NULL` si ce paramètre n'est pas pris en charge.|  
|`IS_LONG`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données est un objet blob qui comporte des données très longues.<br /><br /> `VARIANT_TRUE` indique que le type de données est un `BLOB` qui contient des données très longues ; la définition de données très longues est spécifique au fournisseur.<br /><br /> `VARIANT_FALSE` indique que le type de données n'est pas un `BLOB` comportant des données très longues ou un `BLOB`.<br /><br /> Cette valeur détermine le paramètre de l'indicateur `DBCOLUMNFLAGS_ISLONG` retourné par `GetColumnInfo` dans `IColumnsInfo` et `GetParameterInfo` dans `ICommandWithParameters`.|  
|`BEST_MATCH`|`DBTYPE_BOOL`||Valeur booléenne qui indique si le type de données est une correspondance la plus proche.<br /><br /> `VARIANT_TRUE` indique que le type de données est la correspondance la plus proche entre tous les types de données du magasin de données et le type de données OLE DB indiqué par la valeur de la colonne `DATA_TYPE`.<br /><br /> `VARIANT_FALSE` indique que le type de données n'est pas la correspondance la plus proche.<br /><br /> Pour chaque ensemble de lignes dans lequel la valeur de la colonne `DATA_TYPE` est identique, la colonne `BEST_MATCH` n'a la valeur `VARIANT_TRUE` que dans une seule ligne.|  
|`IS_FIXEDLENGTH`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la colonne a une longueur fixe.<br /><br /> `VARIANT_TRUE` indique que les colonnes de ce type créées par le langage de définition de données (DDL) seront de longueur fixe.<br /><br /> `VARIANT_FALSE` indique que les colonnes de ce type créées par le DDL seront de longueur variable.<br /><br /> Si le champ est `NULL`, le fait que le fournisseur mappe ce champ avec une colonne de longueur fixe ou de longueur variable n'est pas connu.|  
  
 L'ensemble de lignes est trié selon `DATA_TYPE`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DBSCHEMA_PROVIDER_TYPES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`DATA_TYPE`|`DBTYPE_UI2`||  
|`BEST_MATCH`|`DBTYPE_BOOL`||  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB](ole-db-schema-rowsets.md)  
  
  
