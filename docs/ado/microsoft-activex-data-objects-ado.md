---
title: Microsoft ActiveX Data Objects (ADO) | Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, about
ms.assetid: 2fa6237b-44b8-4b6c-9952-5acd80a54e20
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 05cc5d08785b116f4e4dd27b8a0a61b34a14d473
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699397"
---
# <a name="microsoft-activex-data-objects-ado"></a>Microsoft ActiveX Data Objects (ADO)

ADO est utilisé dans les programmes C++ pour vous connecter à SQL Server. Bien sûr, elle fonctionne également pour vous connecter à la base de données SQL Azure dans le cloud.

Chaque section de cet article décrit un composant d’ADO.

> [!NOTE]
> ADO.NET est différente de celle ADO. ADO.NET et de nombreux autres pilotes de connexion SQL et leurs langues, sont abordées en commençant à [pilotes SQL Server](../connect/sql-connection-libraries.md).

  
## <a name="ado"></a>ADO  
 Microsoft ActiveX Data Objects (ADO) activer vos applications clientes accéder et manipuler des données à partir de diverses sources via un fournisseur OLE DB. Ses principaux avantages sont la simplicité d’utilisation, haute vitesse, charge de mémoire faible et une encombrement disque limité. ADO prend en charge les fonctionnalités clés pour la création d’applications Web et client/serveur.  
  
## <a name="ado-md"></a>ADO MD  
 Microsoft ActiveX Data Objects (multidimensionnel) (ADO MD) fournit un accès facile aux données multidimensionnelles à partir de langages tels que Microsoft Visual Basic et Microsoft Visual C++. ADO MD étend Microsoft ActiveX Data Objects (ADO) pour inclure des objets spécifiques aux données multidimensionnelles, tels que les objets CubeDef et Cellset. Avec ADO MD, vous pouvez parcourir un schéma multidimensionnel, un cube de requête et récupérer les résultats.  
  
 Comme ADO, ADO MD utilise un fournisseur OLE DB sous-jacent pour accéder aux données. Pour travailler avec ADO MD, le fournisseur doit être un fournisseur de données multidimensionnelles (MDP) comme défini par la spécification OLE DB pour OLAP. Fournisseurs MDP présente des données dans des vues multidimensionnelles par opposition aux fournisseurs de données tabulaires (TDP) qui présentent les données sous forme de tableaux. Reportez-vous à la documentation de votre fournisseur OLE DB pour OLAP pour des informations plus détaillées sur la syntaxe spécifique et les comportements pris en charge par votre fournisseur.  
  
## <a name="rds"></a>RDS  
 Service de données à distance (RDS) est une fonctionnalité d’ADO, avec lequel vous pouvez déplacer des données à partir d’un serveur vers une application cliente ou d’une page Web, manipuler les données sur le client et retourner des mises à jour sur le serveur dans un seul aller-retour.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="adox"></a>ADOX  
 Microsoft ActiveX Data Objects Extensions pour le langage de définition de données et de sécurité (ADOX) est une extension pour les objets ADO et le modèle de programmation. ADOX inclut des objets pour la création de schémas et de modification, ainsi que de sécurité. S’agissant d’une approche basée sur l’objet de manipulation de schéma, vous pouvez écrire du code qui fonctionne par rapport aux données de différentes sources, quel que soit les différences dans les syntaxes natives.  
  
 ADOX est une bibliothèque complémentaire aux objets ADO principaux. Il expose des objets supplémentaires pour la création, modification et suppression d’objets de schéma, tels que tables et procédures. Il inclut également des objets de sécurité pour gérer les utilisateurs et groupes et pour accorder et révoquer des autorisations sur les objets.  
  
## <a name="documentation"></a>Documentation  
 [Problèmes de conception de la sécurité d’ADO](../ado/guide/ado-security-design-issues.md)  
  
 [Guide du programmeur ADO](../ado/guide/ado-programmer-s-guide.md)  
  
 Présentation de l’utilisation d’ADO, RDS, ADO MD et ADOX.  
  
 [Guide de référence du programmeur ADO](../ado/reference/ado-programmer-s-reference.md)  
  
 Cette section de la documentation ADO contient des rubriques pour chaque ADO, RDS, ADO MD, ADOX objet, collection, propriété, propriété dynamique, méthode, événement et énumération.  
  
 [Glossaire ADO](../ado/ado-glossary.md)  
  
## <a name="support"></a>Support technique  
 Gratuitement aide à ADO problèmes, essayez de validation dans le groupe de discussion public ADO. Ce groupe de discussion est surveillée par des professionnels du support technique Microsoft Product Support Services (PSS) qui couvrent ADO et par d’autres développeurs expérimentés de ADO.  
  
 Vous trouverez plus d’informations sur les options de prise en charge sur le site Web de prendre en charge et de Microsoft Help.


