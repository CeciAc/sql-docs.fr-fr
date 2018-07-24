---
title: STRING_ESCAPE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75eaf0510fc4c897d6ecb473660a71bf31842e7a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051997"
---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Échappe les caractères spéciaux dans les textes et retourne le texte avec des caractères d’échappement. **STRING_ESCAPE** est une fonction déterministe.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>Arguments  
 *texte*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) **nvarchar** représentant l’objet qui doit être échappé.  
  
 *type*  
 Règles d’échappement qui seront appliquées. La valeur prise en charge actuellement est `'json'`.  
  
## <a name="return-types"></a>Types de retour  
 Texte **nvarchar(max)** avec caractères de contrôle et spéciaux d’échappement. Actuellement, **STRING_ESCAPE** peut uniquement échapper les caractères spéciaux JSON répertoriés dans les tableaux suivants.  
  
|Caractère spécial|Séquence codée|  
|-----------------------|----------------------|  
|guillemets (")|\\"|  
|Barre oblique inverse (\\)|\\\|  
|Barre oblique (/)|\\/|  
|Retour arrière|\b|  
|Saut de page|\f|  
|Nouvelle ligne|\n|  
|Retour chariot|\r|  
|Tabulation horizontale|\t|  
  
|Caractère de contrôle|Séquence codée|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>Notes   
  
## <a name="examples"></a>Exemples  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Échapper du texte selon les règles de mise en forme JSON  
 La requête suivante échappe les caractères spéciaux à l’aide des règles JSON et retourne le texte avec séquence d’échappement.  
  
```  
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>B. Mettre en forme un objet JSON  
 La requête suivante crée un texte JSON à partir de variables numériques et de chaîne, et échappe les caractères JSON spéciaux dans les variables.  
  
```  
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',   
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
