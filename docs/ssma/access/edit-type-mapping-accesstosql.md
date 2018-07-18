---
title: Modifier le mappage de Type (AccessToSQL) | Documents Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 7f9d9530-6c04-41d9-bbe7-d91820a30066
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cb67bb417673928114529f9f88530eb00c892de0
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774696"
---
# <a name="edit-type-mapping-accesstosql"></a>Modifier le mappage de Type (AccessToSQL)
Le **modifier le mappage de Type** boîte de dialogue vous permet de spécifier comment les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, le **le mappage de Type** onglet s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Sur le **outils** menu, sélectionnez **les paramètres de projet** ou **les paramètres de projet par défaut**. Dans la boîte de dialogue, sélectionnez **le mappage de Type**. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
Mappages de type spécifique à la table de remplacent la base de données et les mappages de type de projet. Mappage spécifique à la base de données remplace les mappages du projet.  
  
## <a name="options"></a>Options  
**Type de source**  
Sélectionnez le type de données source à mapper à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] type de données.  
  
Si le type de données est de longueur variable, les champs suivants apparaissent sous **type de Source de**:  
  
**From**  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le **texte** type de données, vous pouvez entrer 10 pour indiquer que ce mappage est pour une plage commençant à **text(10)**.  
  
**Pour**  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le **texte** type de données, vous pouvez entrer 20 pour indiquer que ce mappage est pour une plage de fin **text(20)**.  
  
**Type de cible**  
Sélectionnez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] type de données à laquelle le type de source de données est mappé. Lorsque SSMA crée la table ou la procédure stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], le type de source de données passe à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant s’affiche sous **type cible**:  
  
**Replace with**  
Spécifiez la longueur de la cible pour ce mappage. Par exemple, pour le **nvarchar** type de données, vous pouvez entrer 20 pour spécifier que le type de données source spécifiée doit être mappé à **nvarchar (20)**.  
  
