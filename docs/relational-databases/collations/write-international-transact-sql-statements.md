---
title: Rédiger des instructions Transact-SQL internationales | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ab973f34d0bcfb94d3df97e10efcbba69655f8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724737"
---
# <a name="write-international-transact-sql-statements"></a>Rédiger des instructions Transact-SQL internationales
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Les directives suivantes facilitent la transition d'une langue à l'autre des bases de données et applications de bases de données qui utilisent des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , ou leur permettent de prendre en charge directement plusieurs langues :  
  
-   Remplacez toutes les utilisations des types de données **char**, **varchar**et **text** par **nchar**, **nvarchar**et **nvarchar(max)**. Vous réglez ainsi le problème de conversion des pages de codes. Pour plus d’informations, consultez [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Lors des comparaisons et opérations sur les mois et jours de la semaine, utilisez la partie numérique de la date plutôt que les chaînes de noms. Selon les paramètres de langue, des noms de mois et de jours de la semaine différents sont retournés. Par exemple, DATENAME(MONTH,GETDATE()) retourne « May » pour l'anglais (États-Unis), « Mai » pour l'allemand et « mai » pour le français. Utilisez à la place une fonction comme DATEPART qui utilise le numéro du mois plutôt que son nom. Utilisez les noms DATEPART lorsque vous générez des ensembles de résultats qui seront affichés par un utilisateur, car les noms de date sont souvent plus clairs qu'une représentation numérique. Pour autant, ne codez aucun élément logique dépendant des noms affichés d'une langue spécifique.  
  
-   Pour spécifier des dates dans des comparaisons ou comme entrées d'instructions INSERT ou UPDATE, utilisez des constantes qui sont interprétées de la même manière, quelle que soit la langue définie :  
  
    -   Les applications ADO, OLE DB et ODBC doivent utiliser les clauses ODBC d'échappement de temps, de date et d'horodateur :  
  
         **{ ts’** aaaa**-**_mm_**-_** jj**hh_**:**_mm_**:**_ss_[**.**_fff_] **’}** comme : **{ ts’** 1998**-**09**-**24 10**:**02**:**20**’ }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** tel que : **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** tel que : **{ t'** 10:02:20 **'}**  
  
    -   Les applications qui utilisent d'autres API, ou encore des scripts, des procédures stockées ou des déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)] , doivent utiliser les chaînes numériques non séparées. Par exemple, *yyyymmdd* comme 19980924.  
  
    -   Les applications qui utilisent d’autres API, ou encore des scripts, des procédures stockées ou des déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)] , peuvent également utiliser l’instruction CONVERT avec un paramètre de style explicite pour toutes les conversions entre les types de données **time**, **date**, **smalldate**, **datetime**, **datetime2**et **datetimeoffset** et les types de données de chaînes de caractères. Par exemple, l'instruction suivante est interprétée de la même façon, quels que soient les paramètres de connexion concernant la langue et le format de date :  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Pour plus d’informations, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  
