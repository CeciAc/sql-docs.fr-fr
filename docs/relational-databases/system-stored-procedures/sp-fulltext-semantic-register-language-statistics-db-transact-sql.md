---
title: sp_fulltext_semantic_register_language_statistics_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b540d233eeb1eb52a86737372d3d3db6f77a7217
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52417730"
---
# <a name="spfulltextsemanticregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inscrit une base de données de statistiques linguistiques de sémantique pré-remplie dans l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez initialiser l'extraction sémantique uniquement après avoir attaché cette base de données de statistiques linguistiques et l'avoir inscrite à l'aide de cette procédure stockée. Vous ne devez effectuer cette tâche qu'une fois pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] 'database_name';  
GO  
```  
  
##  <a name="Arguments"></a> Arguments  
 [ @dbname =] '*database_name*'  
 Nom de la base de données de statistiques linguistiques de sémantique à inscrire pour l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La base de données doit déjà être attachée. *database_name* est **sysname**, et ne peut pas être NULL.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucun.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La base de données de statistiques linguistiques de sémantique contient des statistiques propres à une langue qui sont obligatoires pour le traitement sémantique d'un contenu textuel.  
  
 **sp_fulltext_semantic_register_language_statistics_db** effectue les étapes suivantes :  
  
1.  Vérifie que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est une version qui prend en charge le traitement sémantique.  
  
2.  Vérifie que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas déjà de base de données de statistiques linguistiques de sémantique définie.  
  
3.  Vérifie que la base de données est une base de données de statistiques linguistiques de sémantique valide.  
  
4.  Définit des autorisations sur la base de données de statistiques linguistiques de sémantique afin de restreindre l'accès à la base de données par les utilisateurs.  
  
5.  Insère les métadonnées qui définissent le nom de la base de données de statistiques linguistiques de sémantique pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
6.  Insère les métadonnées qui définissent les mappages entre la base de données de statistiques linguistiques de sémantique installée et les tables de modèles linguistiques internes.  
  
7.  Vérifie que la base de données est prête à être utilisée.  
  
 Pour plus d’informations, consultez [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur la base de données de statistiques linguistiques de sémantique installée sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], interrogez l’affichage catalogue [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment inscrire la base de données de statistiques linguistiques de sémantique en appelant **sp_fulltext_semantic_register_language_statistics_db**.  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
