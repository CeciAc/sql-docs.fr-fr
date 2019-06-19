---
title: STCurveToLine (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 7f237da350b47ea0c3141709cd82d083ef509196
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939190"
---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une approximation polygonale d’une instance **geography** contenant des segments d’arc de cercle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Retourne une instance **LineString** pour une instance **CircularString** ou **CompoundCurve**.  
  
 Retourne une instance **Polygon** pour une instance **CurvePolygon**.  
  
 Retourne une copie des instances **geography** qui ne contiennent pas d’instances **CircularString**, **CompoundCurve** ou **CurvePolygon**.  
  
 Contrairement à la spécification SQL MM, cette méthode n’utilise pas de valeurs de coordonnées z pour calculer l’approximation polygonale. Les valeurs de coordonnées z présentes dans l’instance **geography** appelante sont ignorées.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne une instance `LineString` qui est une approximation polygonale d'une instance `CircularString` :  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [STLength &#40;type de données geography&#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints &#40;type de données geography&#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
