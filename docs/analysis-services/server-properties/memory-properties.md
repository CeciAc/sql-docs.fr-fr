---
title: Propriétés de mémoire | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b0239d2d203e7cb32a2ea587ee069d26ad003b0e
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854351"
---
# <a name="memory-properties"></a>Propriétés de mémoire
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Préalloue une petite quantité de mémoire au démarrage, afin que les requêtes puissent être traitées immédiatement. De la mémoire supplémentaire est allouée à mesure que les charges de travail de requête et de traitement augmentent. 
  
  En spécifiant des paramètres de configuration, vous pouvez contrôler les seuils auxquels la mémoire est libérée. Par exemple, le paramètre **HardMemoryLimit** spécifie une condition de mémoire insuffisante auto-imposée (par défaut, ce seuil est désactivé), où les nouvelles requêtes sont rejetées en bloc jusqu’à ce que des ressources supplémentaires soient disponibles.

Pour en savoir plus sur la mémoire maximale utilisée par instance d’Analysis Services par édition, consultez [éditions et fonctionnalités prises en charge de SQL Server](../../sql-server/editions-and-components-of-sql-server-2017.md#Cross-BoxScaleLimits).
  
 Sauf indication contraire, les paramètres suivants s’appliquent à la fois en mode serveur tabulaire et multidimensionnelle.  
 
## <a name="default-memory-configuration"></a>Configuration par défaut de la mémoire

Dans la configuration par défaut, chaque instance d’Analysis Services alloue une petite quantité de RAM (40 Mo à 50 Mo) au démarrage, même si l’instance est inactive. 

Rappelez-vous que les paramètres de configuration sont définie par instance. Si vous exécutez plusieurs instances Analysis Services, par exemple une instance multidimensionnelle et une instance tabulaire sur le même matériel, chaque instance alloue sa propre mémoire indépendamment des autres instances.

Le tableau ci-dessous décrit brièvement les paramètres de mémoire les plus couramment utilisés (avec des détails supplémentaires dans la section de référence). Vous devez configurer ces paramètres uniquement si Analysis Services est en concurrence pour la mémoire avec d’autres applications sur le même serveur :

Paramètre | Description
--------|------------
LowMemoryLimit | Pour les instances multidimensionnelles, seuil inférieur auquel le serveur commence tout d’abord à libérer la mémoire allouée aux objets peu fréquemment utilisés.
VertiPaqMemoryLimit | Pour les instances tabulaires, seuil inférieur auquel le serveur commence tout d’abord à libérer la mémoire allouée aux objets peu fréquemment utilisés.
TotalMemoryLimit | Seuil supérieur auquel Analysis Services commence à libérer de la mémoire de façon plus agressive afin de créer de l’espace pour les requêtes qui sont en phase d’exécution, ainsi que pour les nouvelles requêtes à priorité élevée. 
HardMemoryLimit | Autre seuil auquel Analysis Services commence à rejeter en bloc les requêtes en raison d’une sollicitation de la mémoire. 
 
## <a name="property-reference"></a>Référence de propriété

Sauf indication contraire, les propriétés suivantes s’appliquent à la fois aux modes multidimensionnel et tabulaire.

 Les valeurs comprises entre 1 et 100 représentent des pourcentages de **mémoire physique totale** ou d' **espace d'adressage virtuel**, la valeur la plus petite étant retenue. Les valeurs supérieures à 100 représentent les limites de mémoire en octets.
  
 **LowMemoryLimit**  
 Signé 64 bits double précision à virgule flottante numéro propriété qui définit le premier seuil auquel Analysis Services commence à libérer la mémoire pour les objets de faible priorité, comme un cache peu fréquemment utilisé. Une fois la mémoire allouée, le serveur ne libère pas de mémoire en dessous de cette limite. La valeur par défaut est 65, ce qui indique que la limite de mémoire inférieure correspond à 65 % de la mémoire physique ou de l'espace d'adressage virtuel, la valeur inférieure étant applicable.  
  
 **TotalMemoryLimit**  
 Définit un seuil qui, une fois atteint, a pour effet d’indiquer au serveur de désallouer de la mémoire afin de créer de l’espace pour les autres requêtes. Lorsque cette limite est atteinte, l'instance commence lentement à nettoyer la mémoire des caches en fermant les sessions expirées et en déchargeant les calculs non utilisés. La valeur par défaut est 80 % de la mémoire physique ou de l'espace d'adressage virtuel, la valeur inférieure étant applicable. **TotalMemoryLimit** doit toujours être inférieure à **HardMemoryLimit**  
  
 **HardMemoryLimit**  
 Spécifie un seuil de mémoire après lequel l'instance ferme de façon intensive les sessions utilisateur actives pour réduire l'utilisation de la mémoire. Toutes les sessions terminées recevront une erreur indiquant l’annulation par sollicitation de la mémoire. La valeur par défaut, zéro (0), signifie que **HardMemoryLimit** aura une valeur intermédiaire entre **TotalMemoryLimit** et la mémoire physique totale du système ; si la mémoire physique du système est supérieure à l’espace d’adressage virtuel du processus, l’espace d’adressage virtuel est utilisé à la place pour calculer **HardMemoryLimit**.  

**QueryMemoryLimit**   
Azure Analysis Services. Une propriété avancée pour contrôler la quantité de mémoire utilisable par les résultats temporaires au cours d’une requête. S’applique uniquement aux requêtes et les mesures DAX. Requêtes MDX sur des serveurs en mode multidimensionnel n’utilisent pas cette limite. Il ne tient pas compte des allocations de mémoire générale utilisées par la requête. Spécifiée en pourcentage. La valeur par défaut de 0 signifie qu'aucune limite n’est spécifiée.

 **VirtualMemoryLimit**  
  Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **VertiPaqPagingPolicy**  
  Pour les instances tabulaires uniquement, spécifie le comportement de pagination quand la mémoire du serveur est insuffisante. Les valeurs valides sont les suivantes :  
  
  

Paramètre  |Description  
---------|---------
**0**     |  Désactive la pagination. Si la mémoire est insuffisante, le traitement échoue avec une erreur de mémoire insuffisante. Si vous désactivez la pagination, vous devez accorder des privilèges Windows au compte de service. Pour obtenir des instructions, consultez [Configurer les comptes de service &#40;Analysis Services&#41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md). 
**1**     |  (par défaut) Cette propriété active la pagination sur le disque à l’aide du fichier de pagination du système d’exploitation (pagefile.sys).   
  
Lorsque la valeur définie est 1, le traitement est moins susceptible d’échouer en raison des contraintes de mémoire, car le serveur tente de paginer sur le disque à l’aide de la méthode spécifiée. La définition de la propriété **VertiPaqPagingPolicy** ne garantit pas que les erreurs de mémoire ne se produiront pas. Les erreurs de mémoire insuffisante peuvent toujours se produire dans les conditions suivantes :  
  
-   Il n'y a pas assez de mémoire pour tous les dictionnaires. Pendant le traitement, le serveur verrouille les dictionnaires pour chaque colonne dans la mémoire et l’ensemble de ces éléments ne peut pas être supérieure à la valeur spécifiée pour **VertiPaqMemoryLimit**.  
  
-   L'espace d'adressage virtuel est insuffisant pour le processus.  
  
 Pour résoudre les erreurs persistantes de mémoire insuffisante, vous pouvez reconcevoir le modèle pour réduire la quantité de données à traiter, ou bien ajouter plus de mémoire physique à l'ordinateur.  
  
 **VertiPaqMemoryLimit**  
 Pour les instances tabulaires uniquement, si la pagination sur le disque est autorisée, cette propriété indique le niveau de la consommation de mémoire (en pourcentage de la mémoire totale) auquel la pagination démarre. La valeur par défaut est 60. Si la consommation de mémoire est inférieure à 60 %, le serveur ne paginera pas sur le disque. Cette propriété dépend de **VertiPaqPagingPolicyProperty**, qui doit avoir la valeur 1 pour autoriser la pagination.  
  
 **HighMemoryPrice**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryHeapType**  
  Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Les valeurs valides dans SQL Server 2016 SP1 Analysis Services et version ultérieure sont les suivantes :
  
  Paramètre | Description
--------|------------
**-1** | (par défaut) Automatique. Le moteur décidera de l’option à utiliser.
**1** | Segment de mémoire Analysis Services.
**2** | LFH Windows.
**5** | Allocateur hybride. Cet allocateur utilisera LFH Windows pour \<= allocations de 16 Ko et le segment de mémoire pour > allocations de 16 Ko. 
**6** | Allocateur Intel TBB. Disponible dans SQL Server 2016 SP1 Analysis Services (et version ultérieure).
  
  
 **HeapTypeForObjects**  
  Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Les valeurs valides sont les suivantes :
  
   Paramètre | Description
--------|------------
**-1** | (par défaut) Automatique. Le moteur décidera de l’option à utiliser.
**0** | Segment de mémoire LFH Windows.
**1** | Allocateur d’emplacement Analysis Services.
**3** | Chaque objet possède son propre segment de mémoire Analysis Services.

 
 **DefaultPagesCountToReuse**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **HandleIA64AlignmentFaults**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MidMemoryPrice**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MinimumAllocatedMemory**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PreAllocate**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **SessionMemoryLimit**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **WaitCountIfHighMemory**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
