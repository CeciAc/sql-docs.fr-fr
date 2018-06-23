---
title: Propriétés d’informations sur la Source de données | Documents Microsoft
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
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 980e7ea889cc8c95828b4c704748aa6dc2552359
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142711"
---
# <a name="data-source-information-properties"></a>Propriétés des informations de la source de données
  Dans le jeu de propriétés DBPROPSET_SQLSERVERDATASOURCEINFO spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit les propriétés des informations de la source de données.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Type : VT_BOOL<br /><br /> R/W : Read (Lecture)<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : utilisé pour déterminer si le classement des colonnes est pris en charge.<br /><br /> VARIANT_TRUE : le classement au niveau des colonnes est pris en charge.<br /><br /> VARIANT_FALSE : le classement au niveau des colonnes n'est pas pris en charge.|  
|SSPROP_UNICODELCID|Type : VT_I4 R/W: Read (Lecture)<br /><br /> Description : ID des paramètres régionaux Unicode.<br /><br /> Il s'agit des paramètres régionaux utilisés pour le tri des données Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Type : VT_I4 R/W: Read (Lecture)<br /><br /> Description : style de comparaison Unicode.<br /><br /> Options de tri utilisés pour le tri des données Unicode.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERSTREAM spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit la propriété supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Type : VT_BSTR R/W: Read/Write (Lecture/écriture)<br /><br /> Description : le résultat d'une requête FOR XML ne peut pas être un document bien formé. Lorsque cette propriété est spécifiée, le résultat d’un ' sélectionner... for XML' requête est encapsulée dans la balise racine fournie par cette propriété pour retourner un document XML bien formé. Si la requête est exécutée dans le navigateur, il se peut que le navigateur affiche les erreurs de l'analyseur lors du chargement du résultat. Pour éviter l'erreur, SQL ISAPI prend en charge le mot clé ROOT. Ce mot clé est mappé avec la propriété SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets Source de données &#40;OLE DB&#41;](data-source-objects-ole-db.md)  
  
  