---
title: bcp_gettypename | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: afea684549765bac4c24679cc65d74bb4dfa47df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051044"
---
# <a name="bcpgettypename"></a>bcp_gettypename
  Retourne le nom de type de SQL pour un jeton de type BCP spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *jeton*  
 Valeur indiquant un jeton de type BCP.  
  
 *field*  
 Indique si le jeton demandé possède le type max.  
  
## <a name="returns"></a>Valeur renvoyée  
 Chaîne contenant le nom de type SQL qui correspond au type BCP. Si un type BCP non valide est spécifié, une chaîne vide est retournée.  
  
## <a name="remarks"></a>Notes  
 Les jetons de type de BCP sont définis dans le fichier d'en-tête sqlncli.h et la bibliothèque sqlncli11.lib.  
  
 Le tableau suivant spécifie les types BCP possibles, s'ils sont ou pas de type max et la sortie attendue.  
  
|Nom du type BCP|MaxType|Sortie|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|Avant ou après|**decimal**|  
|`SQLNUMERIC`|Avant ou après|**numeric**|  
|`SQLINT1`|Avant ou après|**tinyint**|  
|`SQLINT2`|Avant ou après|**smallint**|  
|`SQLINT4`|Avant ou après|**Int**|  
|`SQLMONEY`|Avant ou après|**money**|  
|`SQLFLT8`|Avant ou après|**float**|  
|`SQLDATETIME`|Avant ou après|**datetime**|  
|`SQLBITN`|Avant ou après|**bit-null**|  
|`SQLBIT`|Avant ou après|**bit**|  
|`SQLBIGCHAR`|non|**char**|  
|`SQLCHARACTER`|non|**char**|  
|`SQLBIGVARCHAR`|non|**varchar**|  
|`SQLVARCHAR`|non|**varchar**|  
|`SQLTEXT`|Avant ou après|**texte**|  
|`SQLBIGBINARY`|non|**binaire**|  
|`SQLBINARY`|non|**Binaire**|  
|`SQLBIGVARBINARY`|non|**Varbinary**|  
|`SQLVARBINARY`|non|**Varbinary**|  
|`SQLIMAGE`|Avant ou après|**Image**|  
|`SQLINTN`|Avant ou après|**int null**|  
|`SQLDATETIMN`|Avant ou après|**datetime-null**|  
|`SQLMONEYN`|Avant ou après|**Money null**|  
|`SQLFLTN`|Avant ou après|**float-null**|  
|`SQLAOPSUM`|Avant ou après|**Sum**|  
|`SQLAOPAVG`|Avant ou après|**Avg**|  
|`SQLAOPCNT`|Avant ou après|**Count**|  
|`SQLAOPMIN`|Avant ou après|**Min**|  
|`SQLAOPMAX`|Avant ou après|**Max**|  
|`SQLDATETIM4`|Avant ou après|**smalldatetime**|  
|`SQLMONEY4`|Avant ou après|**smallmoney**|  
|`SQLFLT4`|Avant ou après|**réel**|  
|`SQLUNIQUEID`|Avant ou après|**uniqueidentifier**|  
|`SQLNCHAR`|non|**NCHAR**|  
|`SQLNVARCHAR`|non|**Nvarchar**|  
|`SQLNTEXT`|Avant ou après|**Ntext**|  
|`SQLVARIANT`|Avant ou après|**sql_variant**|  
|`SQLINT8`|Avant ou après|**Bigint**|  
|`SQLCHARACTER`|Oui|**varchar(max)**|  
|`SQLBIGCHAR`|Oui|**varchar(max)**|  
|`SQLBIGVARCHAR`|Oui|**varchar(max)**|  
|`SQLVARCHAR`|Oui|**varchar(max)**|  
|`SQLBINARY`|Oui|**varbinary(max)**|  
|`SQLBIGBINARY`|Oui|**varbinary(max)**|  
|`SQLBIGVARBINARY`|Oui|**varbinary(max)**|  
|`SQLVARBINARY`|Oui|**varbinary(max)**|  
|`SQLNCHAR`|Oui|**nvarchar(max)**|  
|`SQLNVARCHAR`|Oui|**nvarchar(max)**|  
|`SQLXML`|Oui|**Xml**|  
|`SQLUDT`|Avant ou après|**UDT**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>Prise en charge des fonctionnalités de date et heure améliorées par bcp_gettypename  
 Les valeurs de paramètre de jeton pour les types date/heure sont décrites dans la colonne « Type dans sqlncli.h » de la table dans [modifications de copie en bloc pour les Types améliorées de Date et heure &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). La valeur retournée est dans la ligne correspondante de la colonne « Type de stockage de fichier ».  
  
 Pour plus d’informations, consultez [Date et heure améliorations &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  