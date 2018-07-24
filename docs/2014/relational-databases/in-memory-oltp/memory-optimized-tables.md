---
title: Tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
caps.latest.revision: 65
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6427878b5c032e0560859ab7ba68af8d06fb40e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276545"
---
# <a name="memory-optimized-tables"></a>Tables optimisées en mémoire
  L'OLTP en mémoire[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contribue à améliorer les performances des applications OLTP grâce à un accès rapide aux données optimisées en mémoire, à la compilation en mode natif de la logique métier et aux algorithmes de verrous (internes et externes) gratuits. La fonctionnalité OLTP en mémoire comprend les tables optimisées en mémoire et les types de tables, ainsi que la compilation en mode natif des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] pour permettre un accès efficace à ces tables.  
  
 Pour plus d'informations sur les tables optimisées en mémoire, consultez les rubriques suivantes :  
  
-   [Introduction aux tables optimisées en mémoire](memory-optimized-tables.md)  
  
     Explique de façon détaillée ce que sont les tables optimisées en mémoire et fournit des informations sur la durabilité des données et l'accès aux données dans des tables optimisées en mémoire, ainsi que sur la performance et l'évolutivité.  
  
-   [Compilation en mode natif de tables et de procédures stockées](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     Explique de façon détaillée comment les tables optimisées en mémoire et les procédures stockées compilées en mode natif sont compilées en DLL, et contient des considérations relatives à la sécurité.  
  
-   [Modification des tables optimisées en mémoire](altering-memory-optimized-tables.md)  
  
     Directives pour la mise à jour des tables optimisées en mémoire (y compris la modification des colonnes des tables, des index et de bucket_count).  
  
-   [Comprendre les transactions sur les tables à mémoire optimisée](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     Cette section contient plusieurs rubriques relatives à la réalisation de transactions sur les tables optimisées en mémoire, y compris les niveaux d'isolement des transactions et les transactions multiconteneurs.  
  
-   [Modèle d’application pour partitionner des tables mémoire optimisées](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     Exemple de code détaillé montrant comment émuler des tables partitionnées lors de l'utilisation de tables optimisées en mémoire.  
  
-   [Statistiques pour les tables optimisées en mémoire](statistics-for-memory-optimized-tables.md)  
  
     Explique de façon détaillée comment les statistiques sont compilées pour les tables optimisées en mémoire, et comment gérer et mettre à jour manuellement ces statistiques.  
  
-   [Classements et pages de codes](../../database-engine/collations-and-code-pages.md)  
  
     Explique de façon détaillée les restrictions sur les classements et les pages de codes pris en charge pour les tables optimisées en mémoire.  
  
-   [Taille de la table et des lignes dans les tables mémoire optimisées](table-and-row-size-in-memory-optimized-tables.md)  
  
     Explique de façon détaillée la limite de 8 060 octets sur les lignes des tables optimisées en mémoire et donne un exemple de calcul de la taille d'une table et des lignes.  
  
-   [Guide du traitement des requêtes pour les tables mémoire optimisées](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     Fournit une vue d'ensemble du traitement des requêtes pour les tables optimisées en mémoire et les procédures stockées compilées en mode natif.  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  