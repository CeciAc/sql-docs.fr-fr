---
title: Exécution de procédures stockées (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6329b0ff8f4d502916d2046e404fcecac8fc5869
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73759339"
---
# <a name="stored-procedures---running"></a>Procédures stockées - Exécution
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lorsque vous exécutez des instructions, appeler une procédure stockée sur la source de données (au lieu d'exécuter ou de préparer directement une instruction dans l'application cliente) peut fournir :  
  
-   des performances accrues ;  
  
-   une charge réseau réduite ;  
  
-   une cohérence améliorée ;  
  
-   une précision améliorée ;  
  
-   des fonctionnalités supplémentaires.  
  
 Le fournisseur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB prend en charge trois des mécanismes que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] procédures stockées utilisent pour retourner les données :  
  
-   Chaque instruction SELECT dans la procédure génère un jeu de résultats.  
  
-   La procédure peut retourner des données par l'intermédiaire de paramètres de sortie.  
  
-   La procédure peut avoir un code de retour de type entier.  
  
 L'application doit être en mesure de gérer toutes ces sorties provenant de procédures stockées.  
  
 Des fournisseurs OLE DB différents retournent des paramètres de sortie et des valeurs de retour à des moments différents pendant le traitement des résultats. Dans le cas du fournisseur de OLE DB Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les paramètres de sortie et les codes de retour ne sont pas fournis tant que le consommateur n’a pas récupéré ou annulé les jeux de résultats retournés par la procédure stockée. Les codes de retour et les paramètres de sortie sont retournés dans le dernier paquet TDS provenant du serveur.  
  
 Les fournisseurs utilisent la propriété DBPROP_OUTPUTPARAMETERAVAILABILITY pour signaler quand les paramètres de sortie et les valeurs de retour sont retournés. Cette propriété figure dans le jeu de propriétés DBPROPSET_DATASOURCEINFO.  
  
 Le fournisseur d’OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client définit la propriété DBPROP_OUTPUTPARAMETERAVAILABILITY sur DBPROPVAL_OA_ATROWRELEASE pour indiquer que les codes de retour et les paramètres de sortie ne sont pas retournés tant que le jeu de résultats n’est pas traité ou libéré.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
