---
title: Accéder aux FileTables avec Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c86ab8b3f29699e807c61b571832c106ab235710
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68018890"
---
# <a name="access-filetables-with-transact-sql"></a>Accéder aux FileTables avec Transact-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Décrit le fonctionnement des commandes de langage de manipulation de données (DML) [!INCLUDE[tsql](../../includes/tsql-md.md)] avec des FileTables.  
  
##  <a name="BasicsInsert"></a> Opérations INSERT sur les FileTables  
 Les points suivants s'appliquent aux opérations **INSERT** sur les FileTables :  
  
-   Toutes les colonnes d'attribut de fichier ont des contraintes NOT NULL. Si les valeurs ne sont pas définies explicitement, les valeurs par défaut appropriées sont fournies.  
  
-   Les contraintes définies par le système sont appliquées si l’instruction INSERT définit les valeurs **name**, **path_locator**, **parent_path_locator**, ou les attributs de fichier.  
  
-   L’application peut obtenir la valeur **path_locator** pour un fichier ou un répertoire en fournissant le chemin d’accès au système de fichiers à la fonction [GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md).  
  
##  <a name="BasicsUpdate"></a> Opérations UPDATE sur les FileTables  
 Les points suivants s'appliquent aux opérations **UPDATE** sur les FileTables :  
  
-   Les mises à jour apportées aux données définies par l'utilisateur sont autorisées.  
  
-   Les contraintes définies par le système sont appliquées si l’instruction INSERT définit les valeurs **name**, **path_locator**, **parent_path_locator**, ou les attributs de fichier.  
  
-   Les mises à jour peuvent être apportées aux données FILESTREAM dans la colonne **file_stream** sans affecter aucune des autres colonnes, dont les horodateurs.  
  
##  <a name="BasicsDelete"></a> Opérations DELETE sur les FileTables  
 Les points suivants s'appliquent aux opérations **DELETE** sur les FileTables :  
  
-   La suppression d'une ligne supprime également le fichier ou répertoire correspondant du système de fichiers.  
  
-   La suppression d'une ligne échoue si la ligne correspond à un répertoire qui contient d'autres fichiers ou répertoires.  
  
##  <a name="BasicsConstraints"></a> Contraintes appliquées pour les opérations DML sur les FileTables  
 Les contraintes définies par le système garantissent que les actions DML ne compromettent pas l'intégrité de la hiérarchie de l'espace de noms de fichier. Les contraintes appliquées sont les suivantes :  
  
-   Lorsque vous définissez ou modifiez le **nom** du fichier ou du répertoire :  
  
    -   Les conventions d'affectation des noms de fichiers Windows et de répertoires sont appliquées.  
  
    -   Le système impose l'unicité du nom dans le répertoire parent.  
  
-   Quand vous définissez ou modifiez l’emplacement d’un fichier ou d’un répertoire en définissant ou en modifiant la valeur **path_locator** ou **parent_path_locator**:  
  
    -   L'unicité est appliquée.  
  
    -   La cohérence de l’arborescence hiérarchique des répertoires et des fichiers est appliquée, notamment la cohérence des valeurs **path_locator** et **parent_path_locator** .  
  
-   **is_directory** ne peut pas prendre la valeur True quand la colonne **file_stream** n’est pas Null. Les données de la colonne **file_stream** indiquent que la ligne représente un fichier et pas un répertoire.  
  
-   Les colonnes d'attributs de fichier ne peuvent pas être Null. Les contraintes NOT NULL sont appliquées avec des valeurs par défaut.  
  
-   La valeur de **last_access_time** ne peut pas être antérieure à **last_write_time** et **creation_time**.  
  
## <a name="see-also"></a>Voir aussi  
 [Charger des fichiers dans FileTables](../../relational-databases/blob/load-files-into-filetables.md)   
 [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)   
 [Accéder aux FileTables avec des API d’entrée-sortie de fichier](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)   
 [DDL, fonctions, procédures stockées et vues FileTable](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)  
  
  
