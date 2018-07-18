---
title: Affecter des autorisations de membre de hiérarchie (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: e18ee83a164659904864b84dc80fb21e7f07f463
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305991"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>Affecter des autorisations de membre de hiérarchie (Master Data Services)
  Affectez des autorisations à des membres de la hiérarchie pour permettre à des utilisateurs ou des groupes d’afficher les données dans la zone fonctionnelle **Explorateur** de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Les autorisations des membres de la hiérarchie sont facultatives. Elles améliorent la granularité des autorisations d'objet de modèle, qui sont obligatoires.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-assign-hierarchy-member-permissions"></a>Pour affecter des autorisations de membre de hiérarchie  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Dans la page **Utilisateurs** ou **Groupes** , sélectionnez la ligne de l'utilisateur ou du groupe à modifier.  
  
3.  Cliquez sur **Modifier l'utilisateur sélectionné**.  
  
4.  Cliquez sur l'onglet **Membres de hiérarchie** .  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Dans la liste **Version** , sélectionnez une version.  
  
7.  Dans la liste **Hiérarchie** , sélectionnez une hiérarchie.  
  
8.  Cliquez sur **Modifier**.  
  
9. Développez l'arborescence, puis cliquez sur le nœud de la hiérarchie auquel vous souhaitez affecter des autorisations.  
  
10. Dans le menu, sélectionnez **en lecture seule**, **mise à jour**, ou **Deny**.  
  
11. Cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Les autorisations des membres de la hiérarchie n'entrent pas immédiatement en vigueur. Pour plus d’informations, consultez [Appliquer immédiatement des autorisations de membre &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations des membres de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
