---
title: Associer un paramètre de requête à un paramètre de rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
caps.latest.revision: 47
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: c9d7c519e79330e3295a7d3b3dca1e6a9a131087
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152063"
---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a>Associer un paramètre de requête à un paramètre de rapport (Générateur de rapports et SSRS)
  Lorsque vous définissez une requête de dataset qui contient une variable de requête, la commande de requête est analysée. Pour chaque variable de requête, un paramètre de dataset et un paramètre de rapport correspondants sont créés. Le paramètre de dataset, à son tour, pointe aussi sur le paramètre de rapport. Cela permet à un utilisateur d'entrer une valeur qui passe directement à la requête. Chaque fois que vous modifiez la commande de requête, le même processus a lieu.  
  
 Si vous renommez un paramètre de rapport qui est lié à un paramètre de requête, vous devez lier manuellement les paramètres de requête au paramètre de rapport renommé à l'aide de la procédure de cette rubrique.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a>Pour associer un paramètre de requête à un paramètre de rapport  
  
1.  Dans le volet Données du rapport, cliquez avec le bouton droit sur le dataset, cliquez sur **Propriétés du dataset**, puis sur **Paramètres**.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur l’option **Données du rapport** du menu **Affichage**.  
  
2.  Dans la colonne **Nom du paramètre**, recherchez le nom du paramètre de requête. Les noms de paramètres sont automatiquement renseignés en fonction de la requête. Chaque fois que vous modifiez la requête, la requête est examinée à la recherche de nouveaux paramètres de requête. Les paramètres de requête que vous créez manuellement ne sont pas modifiés lorsque la requête change.  
  
    -   Dans **Nom du paramètre**, recherchez le nom du paramètre de requête tel qu’il existe dans la requête. Vous pouvez également ajouter manuellement un nouveau paramètre de requête et entrer un nom.  
  
    -   Dans **Valeur du paramètre**, tapez ou sélectionnez une expression qui correspond à la valeur à passer au paramètre de requête. Il s'agit en général du nom du paramètre de rapport.  
  
        > [!NOTE]  
        >  Vous n'êtes pas limité aux paramètres de rapport comme valeurs pour les paramètres de requête. Vous pouvez utiliser n'importe quelle expression qui correspond à une valeur possible pour les paramètres.  
  
3.  Répétez l'étape 2 pour indiquer des paramètres de requête supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Concept des paramètres de rapport &#40;rapport Générateur et SSRS&#41;](../report-design/report-parameters-concepts-report-builder-and-ssrs.md)  
  
  