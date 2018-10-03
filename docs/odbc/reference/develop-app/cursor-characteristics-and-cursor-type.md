---
title: Caractéristiques du curseur et le Type de curseur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbef278f3f25b572ddc44e87d60b5cdcd33058c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721057"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Caractéristiques et types de curseurs
Une application peut spécifier les caractéristiques d’un curseur au lieu de spécifier le type de curseur (avant uniquement, statique, commandé par keyset ou dynamique). Pour ce faire, l’application sélectionne la sensibilité et capacité de défilement du curseur (en définissant l’attribut d’instruction SQL_ATTR_CURSOR_SCROLLABLE) (en définissant l’attribut d’instruction SQL_ATTR_CURSOR_SENSITIVITY) avant d’ouvrir le curseur sur l’instruction handle. Le pilote choisit ensuite le type de curseur qui fournit plus efficacement les caractéristiques de l’application demandée.  
  
 Chaque fois qu’une application définit les attributs d’instruction SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY ou SQL_ATTR_CURSOR_TYPE, le pilote apporte les modifications nécessaires pour les autres attributs d’instruction dans cet ensemble de quatre attributs afin que leurs valeurs restent cohérentes. Par conséquent, lorsque l’application spécifie une caractéristique de curseur, le pilote peut modifier l’attribut qui indique le type de curseur en fonction de cette sélection implicite ; Lorsque l’application spécifie un type, le pilote peut modifier tous les autres attributs pour être cohérent avec les caractéristiques du type sélectionné. Pour plus d’informations sur ces attributs d’instruction, consultez la [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) description de fonction.  
  
 Une application qui définit les attributs d’instruction pour spécifier un type de curseur et les caractéristiques de curseur s’exécute le risque d’obtention d’un curseur qui n’est pas la méthode la plus efficace disponible sur ce pilote de répondre aux besoins de l’application.  
  
 Le paramètre implicit des attributs d’instruction est définies par le pilote, à ceci près qu’il doit respecter ces règles :  
  
-   Les curseurs avant uniquement ne sont jamais déroulant ; consultez la définition de SQL_ATTR_CURSOR_SCROLLABLE dans [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Curseurs INSENSITIVE ne sont jamais être mise à jour (et par conséquent, leur accès concurrentiel est en lecture seule) ; Cela est basé sur leur définition de curseurs insensitive dans la norme ISO SQL.  
  
 Par conséquent, le paramètre implicit des attributs d’instruction se produit dans les cas décrits dans le tableau suivant.  
  
|Application affecte à un attribut|Autres attributs définis implicitement|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY avec la valeur SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY aux SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED ou SQL_SENSITIVE, tel que défini par le pilote. Il ne peut jamais être défini avec la valeur SQL_INSENSITIVE, étant donné que les curseurs insensitive sont toujours en lecture seule.|  
|SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou type SQL_CURSOR_DYNAMIC, tel que spécifié par le pilote. Il n’est jamais défini sur SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY avec la valeur SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY à SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE|SQL_ATTR_CONCURRENCY aux SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, SQL_CONCUR_VALUES, tel que spécifié par le pilote. Il n’est jamais défini sur la valeur SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou type SQL_CURSOR_DYNAMIC, tel que spécifié par le pilote.|  
|SQL_ATTR_CURSOR_SENSITIVITY à SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY aux SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, SQL_CONCUR_VALUES, tel que spécifié par le pilote.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN ou type SQL_CURSOR_DYNAMIC, tel que spécifié par le pilote.|  
|SQL_ATTR_CURSOR_TYPE de type SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE à la valeur SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE. (Mais uniquement si SQL_ATTR_CONCURRENCY n’est pas égal à la valeur SQL_CONCUR_READ_ONLY. Les curseurs dynamiques modifiables sont toujours sensibles aux modifications qui ont été apportées dans leur propre transaction.)|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE à la valeur SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED ou SQL_SENSITIVE (critères définis par le pilote, si SQL_ATTR_CONCURRENCY n’est pas SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE à SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE à la valeur SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY avec la valeur SQL_INSENSITIVE (si SQL_ATTR_CONCURRENCY est SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED ou SQL_SENSITIVE (si SQL_ATTR_CONCURRENCY n’est pas SQL_CONCUR_READ_ONLY).|
