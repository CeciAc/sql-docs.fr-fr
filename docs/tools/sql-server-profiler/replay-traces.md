---
title: Relire des traces
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 50ef296f7ce7198dc0e233aca08e33c5f1cf7af0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307459"
---
# <a name="replay-traces"></a>Relire des traces

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La relecture est la capacité de reproduire une activité capturée dans une trace. Lorsque vous créez ou modifiez une trace, vous pouvez enregistrer cette trace dans un fichier pour la relire ultérieurement. Vous pouvez utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour relire l’activité de trace d’un ordinateur unique. Pour les charges de travail importantes, utilisez Distributed Replay Utility pour relire les données de trace de plusieurs ordinateurs.  
  
 Cette section décrit comment utiliser les fonctionnalités de relecture du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Pour plus d’informations sur Distributed Replay Utility, consultez [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contient un moteur de lecture à plusieurs threads capable de simuler les connexions utilisateur et l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La relecture est utile pour résoudre les problèmes d'applications ou de processus. Lorsque vous avez identifié le problème et mis en œuvre les corrections, exécutez la trace qui a détecté le problème potentiel sur l'application ou le processus corrigé. Relisez ensuite la trace d'origine et comparez les résultats.  
  
 Trace replay supports debugging by using the **Toggle Breakpoint** and the **Run to Cursor** options on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu. Ces options améliorent en particulier l'analyse des scripts longs, car elles peuvent diviser la relecture de la trace en segments courts de façon à pouvoir les analyser de manière incrémentielle.  
  
 Pour plus d’informations sur les autorisations nécessaires pour relire des traces, consultez [Autorisations nécessaires pour exécuter SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md)|Décrit les événements qui doivent être inclus dans la définition d'une trace pour qu'elle puisse être relue à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Options de relecture &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-options-sql-server-profiler.md)|Décrit les options que vous pouvez définir dans la boîte de dialogue **Configuration de la relecture** de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Considérations sur la relecture des traces &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/considerations-for-replaying-traces-sql-server-profiler.md)|Décrit les événements de trace qui ne peuvent pas être relus avec le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et les effets de la relecture des traces sur les performances du serveur.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
