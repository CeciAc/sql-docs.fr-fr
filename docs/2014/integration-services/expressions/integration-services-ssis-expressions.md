---
title: Expressions Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], expressions
- Integration Services packages, expressions
- SQL Server Integration Services packages, expressions
- expressions [Integration Services], packages
- SSIS packages, expressions
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2a9d7fe2f1f65f0a698e727e5bad6df392c91546
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62898074"
---
# <a name="integration-services-ssis-expressions"></a>Expressions Integration Services (SSIS)
  Une expression est une combinaison de symboles (identificateurs, littéraux, fonctions et opérateurs) qui génère une seule valeur de données. Les expressions simples peuvent être une constante unique, une variable ou une fonction. Généralement, les expressions sont complexes, car elles utilisent plusieurs opérateurs et fonctions, et référencent plusieurs colonnes et variables. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez utiliser des expressions pour définir des conditions dans les instructions CASE, créer et mettre à jour des valeurs dans des colonnes de données, mettre à jour ou remplir des propriétés au moment de l’exécution, définir des contraintes dans des contraintes de précédence et fournir les expressions utilisées par le conteneur de boucles For.  
  
 Les expressions sont basées sur un langage d'expressions et sur l'évaluateur d'expressions. L'évaluateur d'expression analyse l'expression et détermine si elle respecte les règles du langage d'expressions. Pour plus d'informations sur la syntaxe d'expression, les littéraux et les identificateurs pris en charge, consultez les rubriques suivantes.  
  
-   [Syntaxe &#40;SSIS&#41;](syntax-ssis.md)  
  
-   [Littéraux &#40;SSIS&#41;](numeric-string-and-boolean-literals.md)  
  
-   [Identificateurs &#40;SSIS&#41;](identifiers-ssis.md)  
  
## <a name="components-that-use-expressions"></a>Composants qui utilisent des expressions  
 Les éléments suivants dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peuvent utiliser des expressions :  
  
-   La transformation de fractionnement conditionnel met en œuvre une structure de décision, basée sur des expressions, pour diriger des lignes de données vers différentes destinations. Les expressions utilisées dans une transformation de fractionnement conditionnel doivent s'évaluer à `true` ou à `false`. Par exemple, les lignes qui répondent à la condition dans l'expression « Colonne1 > Colonne2 » peuvent être routées vers une sortie distincte.  
  
-   La transformation de colonne dérivée utilise des valeurs créées au moyen d'expressions, soit pour remplir de nouvelles colonnes dans un flux de données, soit pour mettre à jour des colonnes existantes. Par exemple, l'expression Colonne1 + "ABC" peut être utilisée pour mettre à jour une valeur ou pour créer une nouvelle valeur avec la chaîne concaténée.  
  
-   Les variables utilisent une expression pour définir leur valeur. Par exemple, GETDATE() définit la valeur de la variable comme étant la date actuelle.  
  
-   Les contraintes de précédence peuvent utiliser des expressions pour spécifier les conditions déterminant si le conteneur ou le package contraint est exécuté. Les expressions utilisées dans une contrainte de précédence doivent s'évaluer à `true` ou à `false`. Par exemple, l'expression \@A > \@B compare deux variables définies par l'utilisateur pour déterminer si la tâche contrainte est exécutée.  
  
-   Le conteneur de boucles For peut utiliser des expressions pour créer les instructions d'initialisation, d'évaluation et d'incrémentation utilisées par la structure de bouclage. Par exemple, l'expression \@Counter = 1 initialise le compteur de boucles.  
  
 Les expressions peuvent également être utilisées pour mettre à jour les valeurs des propriétés des packages, les conteneurs tels que les conteneurs de boucles For et Foreach, les tâches, les gestionnaires de connexions aux niveaux des packages et du projet, les modules fournisseurs d'informations et les énumérateurs Foreach. Par exemple, en utilisant une expression de propriété, la chaîne « Localhost.AdventureWorks » peut être affectée à la propriété ConnectionName de la tâche Exécuter SQL. Pour plus d’informations, consultez [Expressions de propriété dans des packages](use-property-expressions-in-packages.md).  
  
## <a name="icon-markers-for-expressions"></a>Marqueurs d'icône pour les expressions  
 Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], un marqueur d'icône spécial s'affiche en regard des gestionnaires de connexions, des variables et des tâches contenant des expressions. La propriété **HasExpressions** est disponible sur tous les objets SSIS qui prennent en charge les expressions, à l’exception des variables. La propriété vous permet d'identifier facilement les objets qui ont des expressions.  
  
## <a name="expression-builder"></a>Générateur d'expressions  
 Le générateur d'expressions est un outil graphique de génération d'expressions. Disponible dans les boîtes de dialogue **Éditeur de transformation de fractionnement conditionnel**, **Éditeur de transformation de colonne dérivée** et **Générateur d’expression** , il s’agit d’un outil graphique qui permet de créer des expressions.  
  
 Le générateur d'expression fournit des dossiers contenant des éléments spécifiques aux packages, et des dossiers contenant les fonctions, les conversions de type et les opérateurs fournis par le langage d'expressions. Les éléments spécifiques aux packages comprennent les variables système et les variables définies par l'utilisateur. Dans les boîtes de dialogue **Éditeur de transformation de fractionnement conditionnel** et **Éditeur de transformation de colonne dérivée** , vous pouvez également afficher des colonnes de données. Pour générer des expressions pour les transformations, vous pouvez faire glisser des éléments des dossiers vers la colonne **Condition** ou **Expression** , ou vous pouvez taper l’expression directement dans la colonne. Le générateur d'expressions ajoute automatiquement les éléments syntaxiques requis, tels que le préfixe \@ des noms des variables.  
  
> [!NOTE]  
>  Les noms des variables définies par l'utilisateur et des variables système respectent la casse.  
  
 Les variables ont une étendue et le dossier **Variables** dans le générateur d’expressions répertorie uniquement les variables qui sont dans l’étendue et utilisables. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 [Utiliser une expression dans un composant de flux de données](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
