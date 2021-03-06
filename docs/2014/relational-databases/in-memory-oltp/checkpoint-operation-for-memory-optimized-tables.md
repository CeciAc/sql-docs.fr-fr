---
title: Opération de point de contrôle pour les tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ddcdec0f624c1d6f70c57e593eaf9da66cbe0419
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63065527"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>Opération de point de contrôle pour les tables mémoire optimisées
  Un point de contrôle doit être effectué régulièrement pour que les données mémoire optimisées dans les fichiers de données/delta puissent anticiper la partie active du journal des transactions. Le point de contrôle permet aux tables mémoire optimisées de restaurer ou récupérer le dernier point de contrôle réussi, puis la partie active du journal des transactions est appliquée pour mettre à jour les tables mémoire optimisées afin de terminer la récupération. Les opérations de point de contrôle des tables sur disque et des tables mémoire optimisées sont des opérations distinctes. La section suivante décrit différents scénarios et le comportement des points de contrôle pour les tables sur disque et les tables mémoire optimisées :  
  
## <a name="manual-checkpoint"></a>Point de contrôle manuel  
 Lorsque vous définissez un point de contrôle manuel, le point de contrôle des tables sur disque et des tables mémoire optimisées est fermé. Le fichier de données actif est fermé même s'il est partiellement rempli.  
  
## <a name="automatic-checkpoint"></a>Point de contrôle automatique  
 Le point de contrôle automatique est implémenté différemment pour les tables sur disque et pour les tables mémoire optimisées en raison des différentes méthodes de persistance des données.  
  
 Pour les tables sur disque, un point de contrôle automatique est pris en fonction de l’option de configuration de l’intervalle de récupération (pour plus d’informations, consultez [Modifier la durée de récupération cible d’une base de données &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)).  
  
 Pour les tables mémoire optimisées, un point de contrôle automatique est pris lorsque la taille du fichier journal des transactions devient supérieure à 512 Mo depuis le dernier point de contrôle. Les 512 Mo incluent les enregistrements du journal des transactions à la fois pour les tables sur disque et les tables mémoire optimisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
