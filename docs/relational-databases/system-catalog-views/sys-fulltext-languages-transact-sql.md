---
title: sys.fulltext_languages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_languages
- sys.fulltext_languages_TSQL
- fulltext_languages
- fulltext_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- languages [full-text search]
- sys.fulltext_languages catalog view
ms.assetid: 2ed6b53d-1cf2-4763-9d58-36ea24a610ef
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e5af224150508f048d91345cba595517209f824d
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73981773"
---
# <a name="sysfulltext_languages-transact-sql"></a>sys.fulltext_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne par langue dont les analyseurs lexicaux sont enregistrés avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque ligne affiche l'identificateur de paramètres régionaux (LCID) et le nom de la langue. Lorsque des analyseurs lexicaux sont inscrits pour une langue, ses autres ressources linguistiques (générateurs de formes dérivées, mots parasites (mots vides) et fichiers de dictionnaire des synonymes) sont disponibles pour les opérations d’indexation et d’interrogation de texte intégral. La valeur du **nom** ou du **LCID** peut être spécifiée dans les requêtes de texte intégral et l’index de recherche en texte intégral [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions.  
   
|Colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|**lcid**|**int**|Identificateur des paramètres régionaux (LCID) [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows de la langue.|  
|**nom**|**sysname**|Valeur de l’alias dans [sys. syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) qui correspond à la valeur de **LCID** ou à la représentation sous forme de chaîne du LCID numérique.|  
  
## <a name="values-returned-for-default-languages"></a>Valeurs retournées pour les langues par défaut  
 Le tableau suivant présente uniquement les valeurs des langues dont les analyseurs lexicaux sont inscrits par défaut.  
  
|Langue|LCID|  
|--------------|----------|  
|Arabic|1025|  
|Bengali (India)|1093|  
|British English|2057|  
|Bulgarian|1026|  
|Catalan|1027|  
|Chinois (Hong Kong R.A.S., RPC)|3076|  
|Chinese (Macao SAR)|5124|  
|Chinese (Singapore)|4100|  
|Croatian|1050|  
|Czech|1029|  
|Danois|1030|  
|Dutch|1043|  
|English|1033|  
|French|1036|  
|German|1031|  
|**S’applique à** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Greek|1032|  
|Gujarati|1095|  
|Hebrew|1037|  
|Hindi|1081|  
|Icelandic|1039|  
|Indonesian|1057|  
|Italian|1040|  
|Japanese|1041|  
|Kannada|1099|  
|Korean|1042|  
|Latvian|1062|  
|Lithuanian|1063|  
|Malay - Malaysia|1086|  
|Malayalam|1 100|  
|Marathi|1102|  
|Neutral|0|  
|Norwegian (Bokmål)|1044|  
|**S’applique à** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Polish|1045|  
|Portuguese (Brazil)|1046|  
|Portuguese (Portugal)|2070|  
|Punjabi|1094|  
|Romanian|1048|  
|Russian|1049|  
|Serbian (Cyrillic)|3098|  
|Serbian (Latin)|2074|  
|Simplified Chinese|2052|  
|Slovak|1051|  
|Slovenian|1060|  
|Spanish|3082|  
|Swedish|1053|  
|Tamil|1097|  
|Télougou|1098|  
|Thai|1054|  
|Traditional Chinese|1028|  
|**S’applique à** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Turkish|1055|  
|Ukrainian|1058|  
|Urdu|1056|  
|Vietnamese|1066|  
  
## <a name="remarks"></a>Notes  
 Pour mettre à jour la liste des langues inscrites avec la recherche en texte intégral, utilisez [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**'.  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Mise à niveau de la fonction de recherche en texte intégral](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
