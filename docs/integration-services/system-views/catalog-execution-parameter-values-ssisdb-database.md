---
title: catalog.execution_parameter_values (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7ebe5d9e8ec650a05eb92667dbf5d357965352e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658645"
---
# <a name="catalogexecutionparametervalues-ssisdb-database"></a>catalog.execution_parameter_values (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les valeurs de paramètre effectives utilisées par les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pendant une instance d'exécution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|Identificateur (ID) unique du paramètre d'exécution.|  
|execution_id|**bigint**|ID unique de l'instance d'exécution.|  
|object_type|**smallint**|Lorsque la valeur est `20`, le paramètre est un paramètre de projet. Lorsque la valeur est `30`, le paramètre est un paramètre de package. Quand la valeur est `50`, le paramètre est l’un des éléments suivants :<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **SYNCHRONIZED**|  
|parameter_data_type|**nvarchar(128)**|Type de données du paramètre.|  
|parameter_name|**sysname**|Nom du paramètre.|  
|parameter_value|**sql_variant**|Valeur du paramètre. Quand sensitive est `0`, la valeur en texte en clair est indiquée. Quand sensitive est `1`, la valeur **NULL** s’affiche.|  
|sensible|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est sensible. Lorsque la valeur est `0`, la valeur de paramètre n'est pas sensible.|  
|required|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est obligatoire pour démarrer l'exécution. Lorsque la valeur est `0`, la valeur de paramètre n'est pas obligatoire pour démarrer l'exécution.|  
|value_set|**bit**|Lorsque la valeur est `1`, la valeur de paramètre a été affectée. Lorsque la valeur est `0`, la valeur de paramètre n'a pas été affectée.|  
|runtime_override|**bit**|Lorsque la valeur est `1`, la valeur d'origine a été modifiée avant le démarrage de l'exécution. Lorsque la valeur est `0`, la valeur de paramètre est la valeur d'origine définie.|  
  
## <a name="remarks"></a>Notes   
 Cette vue affiche une ligne pour chaque paramètre d'exécution dans le catalogue. Une valeur de paramètre d'exécution est la valeur affectée à un paramètre du projet ou à un paramètre du package pendant une instance d'exécution unique.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
