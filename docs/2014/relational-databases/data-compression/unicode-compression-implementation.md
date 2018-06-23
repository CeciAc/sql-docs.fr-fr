---
title: Implémentation de la compression Unicode | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-data-compression
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 53c1b66b26fe785fe932870f02ff67326c335e31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051058"
---
# <a name="unicode-compression-implementation"></a>Implémentation de la compression Unicode
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise une implémentation de l’algorithme SCSU (Standard Compression Scheme for Unicode) pour compresser les valeurs Unicode stockées dans des objets à compression de ligne ou de page. Pour ces objets compressés, la compression Unicode est automatique pour les colonnes `nchar(n)` et `nvarchar(n)`. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] stocke les données Unicode comme 2 octets, indépendamment des paramètres régionaux. Ceci porte le nom d'encodage UCS-2. Pour certains paramètres régionaux, l'implémentation de la compression SCSU dans SQL Server peut économiser jusqu'à 50 pour cent d'espace de stockage.  
  
## <a name="supported-data-types"></a>Types de données pris en charge  
 La compression Unicode prend en charge les types de données de longueur fixe `nchar(n)` et `nvarchar(n)`. Les valeurs de données stockées hors ligne ou dans des colonnes `nvarchar(max)` ne sont pas compressées.  
  
> [!NOTE]  
>  La compression Unicode n’est pas pris en charge pour `nvarchar(max)` même si elle est stockée dans la ligne de données. Toutefois, ce type de données peut tirer parti de la compression de page.  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a>Mise à niveau à partir de versions antérieures de SQL Server  
 Lorsqu'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les modifications liées à la compression Unicode ne sont apportées à aucun objet de base de données, compressé ou non compressé. Une fois la base de données mise à niveau, les objets sont affectés comme suit :  
  
-   Si l'objet n'est pas compressé, aucune modification n'est apportée et l'objet continue de fonctionner comme précédemment.  
  
-   Les objets à compression de page ou de ligne continuent de fonctionner comme précédemment. Les données non compressés restent sous forme non compressée jusqu'à ce que leur valeur soit mise à jour.  
  
-   Les nouvelles lignes insérées dans une table à compression de page ou de ligne sont compressées à l'aide de la compression Unicode.  
  
    > [!NOTE]  
    >  Pour tirer pleinement parti des avantages de la compression Unicode, l'objet doit être reconstruit avec compression de ligne ou de page.  
  
## <a name="how-unicode-compression-affects-data-storage"></a>Impact de la compression Unicode sur le stockage des données  
 Lorsqu'un index est créé ou reconstruit ou lorsqu'une valeur est modifiée dans une table compressée avec la compression de page ou de ligne, l'index ou la valeur affecté est stockée sous forme compressée uniquement si sa taille compressée est inférieure à sa taille actuelle. Cela empêche que la taille des lignes dans une table ou un index n'augmente à cause de la compression Unicode.  
  
 L'espace de stockage économisé par la compression dépend des caractéristiques des données compressées et des paramètres régionaux des données. Le tableau suivant répertorie les économies d'espace qui peuvent être accomplies pour plusieurs paramètres régionaux.  
  
|Paramètres régionaux|Pourcentage de compression|  
|------------|-------------------------|  
|Anglais|50|  
|German|50|  
|Hindi|50|  
|Turc|48|  
|Vietnamien|39|  
|Japonais|15|  
  
## <a name="see-also"></a>Voir aussi  
 [Compression de données](data-compression.md)   
 [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql)   
 [Implémentation de la compression de page](page-compression-implementation.md)   
 [sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
