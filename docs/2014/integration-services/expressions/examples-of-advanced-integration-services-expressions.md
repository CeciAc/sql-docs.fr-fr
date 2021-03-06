---
title: Exemples d’expressions Integration Services avancées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9272a6c11ce226f385c0b1f79f965a2a0f55835e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62901120"
---
# <a name="examples-of-advanced-integration-services-expressions"></a>Exemples d'expressions Integration Services avancées
  Cette section donne des exemples d'expressions avancées qui combinent plusieurs opérateurs et fonctions. Si une expression est utilisée dans une contrainte de priorité ou dans la transformation de fractionnement conditionnel, elle doit renvoyer une valeur booléenne. Toutefois, cette restriction ne s'applique pas aux expressions utilisées dans les expressions de propriété, les variables, la transformation de colonne dérivée ou le conteneur de boucles For.  
  
 Les exemples suivants utilisent les bases de données **AdventureWorks** et [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Chaque exemple indique les tables utilisées.  
  
## <a name="boolean-expressions"></a>Expressions booléennes  
  
-   L’exemple suivant utilise la table **Product** . L’expression évalue l’entrée du mois dans la colonne **SellStartDate** et retourne TRUE si le mois est Juin ou un mois ultérieur.  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   L’exemple suivant utilise la table **Product** . L’expression évalue le résultat arrondi de la division de la colonne **ListPrice** par la colonne **StandardCost** et retourne TRUE si le résultat est supérieur à 1,5.  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   L’exemple suivant utilise la table **Product** . L'expression renvoie TRUE si les trois opérations produisent la valeur TRUE. Si la colonne **Size** et la variable **BikeSize** ont des types de données incompatibles, l’expression requiert une conversion explicite, comme le montre le deuxième exemple. La conversion vers le type de données DT_WSTR comprend la longueur de la chaîne.  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   L’exemple suivant utilise la table **CurrencyRate** . L'expression compare des valeurs de tables et de variables. Elle retourne TRUE si les entrées des colonnes **FromCurrencyCode** ou **ToCurrencyCode** sont égales aux valeurs des variables et si la valeur de **AverageRate** est supérieure à celle de **EndOfDayRate**.  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   L’exemple suivant utilise la table **Currency** . L’expression retourne TRUE si le premier caractère de la colonne **Name** n’est pas « a » ou « A ».  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     L'expression suivante donne le même résultat, mais elle est plus efficace car seul un caractère est converti en majuscule.  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a>Expressions non booléennes  
 Les expressions non booléennes sont utilisées dans la transformation de colonne dérivée, les expressions de propriété et le conteneur de boucles For.  
  
-   L’exemple suivant utilise la table **Contact** . L’expression supprime les espaces de début et de fin des colonnes **FirstName**, **MiddleName**et **LastName** . Elle extrait la première lettre de la colonne **MiddleName** si elle n’est pas égale à Null, concatène l’initiale de milieu et les valeurs des colonnes **FirstName** et **LastName**et insère les espaces appropriés entre les valeurs.  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   L’exemple suivant utilise la table **Contact** . L’expression valide les entrées de la colonne **Salutation** . Elle retourne une entrée **Salutation** ou une chaîne vide.  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   L’exemple suivant utilise la table **Product** . L’expression convertit le premier caractère de la colonne **Color** en majuscules et les autres caractères en minuscules.  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   L’exemple suivant utilise la table **Product** . L’expression calcule le nombre de mois pendant lesquels un produit a été vendu et retourne la chaîne « Unknown » si la colonne **SellStartDate** ou **SellEndDate** contient une valeur NULL.  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   L’exemple suivant utilise la table **Product** . L’expression calcule la marge sur la colonne **StandardCost** et arrondit le résultat avec une précision de deux. Le résultat est exprimé en pourcentage.  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a>Tâches associées  
 [Utiliser une expression dans un composant de flux de données](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), sur pragmaticworks.com  
  
  
