---
title: Paramètres du projet (mappage de Type) (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: beb82f2fd894af71bb6f291dcc6f86a995f8dd85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138328"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Paramètres du projet (Mappage de type) (MySQLToSQL)
Les paramètres de mappage de Type de projet vous permettent de définir des mappages de type par défaut pour le projet SSMA.  

Mappage de type est disponible dans les boîtes de dialogue Paramètres du projet et les paramètres de projet par défaut :  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de mappage de type, dans le menu Outils, sélectionnez les paramètres du projet, puis cliquez sur le mappage de Type dans le volet gauche.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Pour accéder au mappage de type paramètres, dans le menu Outils, sélectionnez les paramètres de projet par défaut, type de projet de migration Sélectionnez pour lequel les paramètres sont requis pour être affiché / a été remplacée par **Version cible de Migration** liste déroulante, puis cliquez sur Type Mappage dans le volet gauche.  
  
## <a name="options"></a>Options  
  
##### <a name="source-type"></a>Type de source  
Il est le type de données MySQL, qui doit être mappé au type de données de base de données cible.  
  
##### <a name="target-type"></a>Type de cible  
Type de la base de données cible pour le type de données MySQL spécifié.  
  
##### <a name="add"></a>Ajouter  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
##### <a name="edit"></a>Modifier  
Cliquez pour modifier le type de données sélectionné dans la liste de mappage.  
  
##### <a name="remove"></a>Supprimer  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
##### <a name="reset-to-default"></a>Rétablir les valeurs par défaut  
Cliquez pour réinitialiser la liste de mappage de type pour les valeurs par défaut SSMA.  
  
## <a name="type-mappings"></a>Mappages de types  
Le tableau suivant présente le mappage par défaut entre les types de données source et cible  
  
|||  
|-|-|  
|**Type de données de MySQL**|**Type de données SQL Server**|  
|bigint|bigint|  
|bigint [*.. 255]|bigint|  
|binary|binaire [1]|  
|binaire [valeur 0.. 1]|binaire [1]|  
|binaire [2..255]|binaire [*]|  
|bit|binaire [1]|  
|bits [0..8]|binaire [1]|  
|bits [17..24]|binaire [3]|  
|bits [25..32]|binaire [4]|  
|bits [33..40]|binaire [5]|  
|bits [41..48]|binaire [6]|  
|bits [49..56]|binaire [7]|  
|bits [57..64]|binaire [8]|  
|bits [9..16]|binaire [2]|  
|objet blob|varbinary(max)|  
|objet BLOB de [valeur 0.. 1]|varbinary [1]|  
|objet BLOB [2..8000]|varbinary [*]|  
|objet BLOB [8001.. *]|varbinary(max)|  
|bool|bit|  
|booléenne|bit|  
|char|nchar[1]|  
|octets de char|binaire [1]|  
|octets de char [valeur 0.. 1]|binaire [1]|  
|octets de char [2..255]|binaire [*]|  
|Char [valeur 0.. 1]|nchar[1]|  
|Char [2..255]|nchar[*]|  
|caractère|nchar[1]|  
|caractère variable la [valeur 0.. 1]|nvarchar[1]|  
|caractère variable [2..255]|nvarchar|  
|caractère [valeur 0.. 1]|nchar[1]|  
|caractère [2..255]|nchar[*]|  
|date|date|  
|datetime|datetime2[0]|  
|dec|décimal|  
|DEC [*.. 65]|Decimal [*] [0]|  
|DEC [*.. 65] [\*... 30]|decimal[*][\*]|  
|décimal|décimal|  
|Decimal [*.. 65]|Decimal [*] [0]|  
|Decimal [*.. 65] [\*... 30]|decimal[*][\*]|  
|Double|float [53]|  
|double précision|float [53]|  
|double précision [*.. 255] [\*... 30]|numérique [*] [\*]|  
|double [*.. 255] [\*... 30]|numérique [*] [\*]|  
|fixe|numeric|  
|fixe [*.. 65] [\*... 30]|numérique [*] [\*]|  
|float|float [24]|  
|float [*.. 255] [\*... 30]|numérique [*] [\*]|  
|float [*.. 53]|float [53]|  
|int|int|  
|int [*.. 255]|int|  
|entier|int|  
|entier [*.. 255]|int|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|int|  
|mediumint [*.. 255]|int|  
|mediumtext|nvarchar(max)|  
|national char|nchar[1]|  
|national char [valeur 0.. 1]|nchar[1]|  
|national char [2..255]|nchar[*]|  
|caractères nationaux|nchar[1]|  
|variable de caractères nationaux|nvarchar[1]|  
|caractères nationaux faire varier la [valeur 0.. 1]|nvarchar[1]|  
|caractères nationaux varying [2..4000]|nvarchar[*]|  
|variable de caractères nationaux [4001.. *]|nvarchar(max)|  
|caractères nationaux [valeur 0.. 1]|nchar[1]|  
|caractères nationaux [2..255]|nchar[*]|  
|national varchar|nvarchar[1]|  
|national varchar [valeur 0.. 1]|nvarchar[1]|  
|national varchar [2..4000]|nvarchar[*]|  
|national varchar [4001.. *]|nvarchar(max)|  
|nchar|nchar[1]|  
|NCHAR varchar|nvarchar[1]|  
|NCHAR, varchar [valeur 0.. 1]|nvarchar[1]|  
|NCHAR, varchar [2..4000]|nvarchar[*]|  
|NCHAR varchar [4001.. *]|nvarchar(max)|  
|NCHAR [valeur 0.. 1]|nchar[1]|  
|NCHAR [2..255]|nchar[*]|  
|numeric|numeric|  
|numérique [*.. 65]|numérique [*] [0]|  
|numérique [*.. 65] [\*... 30]|numérique [*] [\*]|  
|nvarchar|nvarchar[1]|  
|nvarchar [valeur 0.. 1]|nvarchar[1]|  
|nvarchar [2..4000]|nvarchar[*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|real|float [53]|  
|réel [*.. 255] [\*... 30]|numérique [*] [\*]|  
|serial|bigint|  
|smallint|smallint|  
|smallint [*.. 255]|smallint|  
|text|nvarchar(max)|  
|texte [valeur 0.. 1]|nvarchar[1]|  
|texte [2..4000]|nvarchar[*]|  
|texte [4001.. *]|nvarchar(max)|  
|time|time|  
|timestamp|datetime|  
|tinyblob|varbinary [255]|  
|tinyint|smallint|  
|tinyint [*.. 255]|smallint|  
|tinytext|nvarchar [255]|  
|valeurs bigint non signées|bigint|  
|valeurs bigint non signées [*.. 255]|bigint|  
|dec non signé|décimal|  
|non signé dec [*.. 65]|Decimal [*] [0]|  
|non signé dec [*.. 65] [\*... 30]|decimal[*][\*]|  
|décimal non signé|décimal|  
|décimal non signé [*.. 65]|Decimal [*] [0]|  
|décimal non signé [*.. 65] [\*... 30]|decimal[*][\*]|  
|double non signé|float [53]|  
|double précision non signée|float [53]|  
|unsigned double précision [*.. 255] [\*... 30]|numérique [*] [\*]|  
|unsigned double [*.. 255] [\*... 30]|numérique [*] [\*]|  
|unsigned fixe|numeric|  
|unsigned fixe [*.. 65] [\*... 30]|numérique [*] [\*]|  
|float non signé|float [24]|  
|non signé float [*.. 255] [\*... 30]|numérique [*] [\*]|  
|non signé float [*.. 53]|float [53]|  
|nombre entier non signé|bigint|  
|unsigned int [*.. 255]|bigint|  
|entier non signé|bigint|  
|entier non signé [*.. 255]|bigint|  
|mediumint non signé|int|  
|mediumint non signé [*.. 255]|int|  
|numérique non signé|numeric|  
|numérique non signée [*.. 65]|numérique [*] [0]|  
|numérique non signée [*.. 65] [\*... 30]|numérique [*] [\*]|  
|non signé réel|float [53]|  
|unsigned réel [*.. 255 [[\*... 30]|numérique [*] [\*]|  
|smallint non signé|int|  
|smallint non signé [*.. 255]|int|  
|tinyint non signé|tinyint|  
|tinyint non signée [*.. 255]|tinyint|  
|varbinary [valeur 0.. 1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [valeur 0.. 1]|nvarchar[1]|  
|varchar [2..4000]|nvarchar[*]|  
|varchar [4001.. *]|nvarchar(max)|  
|year|smallint|  
|année [2..2]|smallint|  
|année [4..4]|smallint|  
  
##### <a name="add"></a>Ajouter  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
##### <a name="edit"></a>Modifier  
Cliquez pour modifier un type de données dans la liste de mappage.  
  
##### <a name="remove"></a>Supprimer  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
##### <a name="reset-to-default"></a>Rétablir les valeurs par défaut  
Cliquez pour réinitialiser tous les mappages de type de données pour les valeurs par défaut SSMA.  
  
