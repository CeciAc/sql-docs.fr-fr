---
title: Sys.fn_cdc_map_time_to_lsn (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_map_time_to_lsn
- fn_cdc_map_time_to_lsn_TSQL
- sys.fn_cdc_map_time_to_lsn_TSQL
- fn_cdc_map_time_to_lsn
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_map_time_to_lsn
- sys.fn_cdc_map_time_to_lsn
ms.assetid: 6feb051d-77ae-4c93-818a-849fe518d1d4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c22074e686f9dff1d988d7453c0c546fa6e049b5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399933"
---
# <a name="sysfncdcmaptimetolsn-transact-sql"></a>sys.fn_cdc_map_time_to_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur de numéro séquentiel de séquence de journal dans le **start_lsn** colonne dans le [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) (table système) pour l’heure spécifiée. Vous pouvez utiliser cette fonction pour mapper systématiquement des plages de date/heure dans la plage de LSN requise par les fonctions d’énumération de capture de données modifiées [cdc.fn_cdc_get_all_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) et [cdc.fn _cdc_get_net_changes_ < instance_capture >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md) pour renvoyer les modifications de données dans cette plage.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_cdc_map_time_to_lsn ( '<relational_operator>', tracking_time )  
  
<relational_operator> ::=  
{  largest less than  
 | largest less than or equal  
 | smallest greater than  
 | smallest greater than or equal  
}  
```  
  
## <a name="arguments"></a>Arguments  
 **«**< relational_operator >**'** {plus grande moins que | plus moins grand qu’ou égal | plus petit supérieur à | plus petit supérieur ou égal}  
 Est utilisé pour identifier une valeur LSN distincte dans le **cdc.lsn_time_mapping** table avec associé à un **tran_end_time** qui satisfait la relation par rapport à la *tracking_time*  valeur.  
  
 *relational_operator* est **nvarchar (30)**.  
  
 *tracking_time*  
 Valeur datetime à mettre en correspondance. *tracking_time* est **datetime**.  
  
## <a name="return-type"></a>Type de retour  
 **binary(10)**  
  
## <a name="remarks"></a>Notes  
 Pour comprendre comment la **sys.fn_cdc_map_time_lsn** peut être utilisé pour mapper les plages datetime aux plages LSN, considérez le scénario suivant. Supposez qu'un utilisateur souhaite extraire des données de modifications de façon quotidienne. Autrement dit, il ne souhaite extraire que les modifications pour un jour donné jusqu'à minuit compris. La limite inférieure de la plage temporelle se situerait à minuit, sans l'inclure, le jour précédent. La limite supérieure se situerait à minuit (compris) le jour donné. L’exemple suivant montre comment la fonction **sys.fn_cdc_map_time_to_lsn** peut être utilisé pour mapper systématiquement cette plage temporelle dans la plage basée sur LSN nécessaire par les fonctions d’énumération de capture de données modifiées pour retourner toutes les modifications dans cette plage.  
  
 `DECLARE @begin_time datetime, @end_time datetime, @begin_lsn binary(10), @end_lsn binary(10);`  
  
 `SET @begin_time = '2007-01-01 12:00:00.000';`  
  
 `SET @end_time = '2007-01-02 12:00:00.000';`  
  
 `SELECT @begin_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than', @begin_time);`  
  
 `SELECT @end_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);`  
  
 `SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@begin_lsn, @end_lsn, 'all` `');`  
  
 L'opérateur relationnel '`smallest greater than`' est utilisé pour limiter les modifications à celles qui ont été effectuées après minuit le jour précédent. Si plusieurs entrées avec différentes valeurs LSN partage le **tran_end_time** valeur identifiée comme limite inférieure dans le [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) table, la fonction retournera la valeur LSN la vérification toutes les entrées sont incluses. Pour la limite supérieure, l’opérateur relationnel '`largest less than or equal to`' permet de s’assurer que la plage comprend toutes les entrées pour le jour, y compris ceux qui ont minuit comme leurs **tran_end_time** valeur. Si plusieurs entrées avec différentes valeurs LSN partage le **tran_end_time** valeur identifiée comme limite supérieure, la fonction retournera le LSN la plus élevée qui garantit que toutes les entrées sont incluses.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le `sys.fn_cdc_map_time_lsn` fonction permettant de déterminer s’il existe des lignes dans le [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) table avec un **tran_end_time** valeur est supérieure ou égale à minuit. Cette requête peut être utilisée pour déterminer, par exemple, si le processus de capture a déjà traité les modifications validées jusqu'à minuit le jour précédent, afin que l'extraction des données de modifications pour ce jour puisse continuer.  
  
```  
DECLARE @extraction_time datetime, @lsn binary(10);  
SET @extraction_time = '2007-01-01 12:00:00.000';  
SELECT @lsn = sys.fn_cdc_map_time_to_lsn ('smallest greater than or equal', @extraction_time);  
IF @lsn IS NOT NULL  
BEGIN  
<some action>  
END  
```  
  
## <a name="see-also"></a>Voir aussi  
 [cdc.lsn_time_mapping &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys.fn_cdc_map_lsn_to_time &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
