---
title: sys.fn_all_changes_&lt;capture_instance&gt; (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_all_changes
- sys.fn_all_changes
- fn_all_changes_TSQL
- sys.fn_all_changes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_all_changes_<capture_instance>
- sys.fn_all_changes_<capture_instance>
ms.assetid: 564fae96-b88c-4f22-9338-26ec168ba6f5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 40bf73a1cdca0bc582ac3e6ed6a977980d2aa24f
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67585109"
---
# <a name="sysfnallchangesltcaptureinstancegt-transact-sql"></a>sys.fn_all_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wrappers pour le **toutes les modifications** fonctions de requête. Les scripts requis pour créer ces fonctions sont générés par la procédure stockée sys.sp_cdc_generate_wrapper_function.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn_all_changes_<capture_instance> ('start_time' ,'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all update old  
}  
```  
  
## <a name="arguments"></a>Arguments  
 *start_time*  
 Le **datetime** valeur qui représente le point de terminaison inférieur de la plage d’entrées de table de modifications à inclure dans le jeu de résultats.  
  
 Seules les lignes dans la capture de données modifiées. < instance_capture > _CT modifications table qui a une heure de validation associée supérieure à *start_time* sont inclus dans le jeu de résultats.  
  
 Si une valeur NULL est fournie pour cet argument, le point de terminaison inférieur de la plage de requêtes correspond au point de terminaison inférieur de la plage valide pour l'instance de capture.  
  
 *end_time*  
 Le **datetime** valeur qui représente le point de terminaison supérieur de la plage d’entrées de table de modifications à inclure dans le jeu de résultats.  
  
 Ce paramètre peut prendre une des deux significations possibles, selon la valeur choisie pour @closed_high_end_point lorsque sys.sp_cdc_generate_wrapper_function est appelé pour générer le script de création pour la fonction wrapper :  
  
-   @closed_high_end_point = 1  
  
     Seules les lignes dans la table de modifications cdc. < instance_capture > _CT qui ont un associé heure de validation inférieure ou égale à end_time sont incluses dans le jeu de résultats...  
  
-   @closed_high_end_point = 0  
  
     Seules les lignes dans le CDC.instance_capture_ct table de modifications qui ont une heure de validation associée strictement inférieure à end_time sont incluses dans le résultat défini.  
  
 Si une valeur NULL est fournie pour cet argument, le point de terminaison supérieur de la plage de requêtes correspond au point de terminaison supérieur de la plage valide pour l'instance de capture.  
  
 < row_filter_option > :: = {toutes les | tous les mettre à jour ancien}  
 Option qui régit le contenu des colonnes de métadonnées ainsi que les lignes retournées dans le jeu de résultats.  
  
 Il peut s'agir de l'une des options suivantes :  
  
 all  
 Retourne toutes les modifications dans la plage spécifiée de numéro séquentiel dans le journal. Pour les modifications résultantes d'une opération de mise à jour, cette option retourne seulement la ligne qui contient les nouvelles valeurs après l'application de la mise à jour.  
  
 all update old  
 Retourne toutes les modifications dans la plage spécifiée de numéro séquentiel dans le journal. Pour les modifications résultantes d'une opération de mise à jour, cette option retourne seulement les deux lignes qui contiennent les valeurs de colonnes avant et après la mise à jour.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de colonne|Description|  
|-----------------|-----------------|-----------------|  
|__CDC_STARTLSN|**binary(10)**|Numéro LSN de validation de la transaction associée à la modification. Toutes les modifications validées dans la même transaction partagent le même numéro LSN de validation.|  
|__CDC_SEQVAL|**binary(10)**|Valeur de classement utilisée pour classer les modifications de ligne dans une transaction.|  
|\<colonnes de @column_list>|**Varie**|Les colonnes qui sont identifiées dans le *column_list* l’argument de sp_cdc_generate_wrapper_function lorsqu’elle est appelée pour générer le script qui crée la fonction wrapper.|  
|__CDC_OPERATION|**nvarchar(2)**|Code d'opération qui indique l'opération requise pour appliquer la ligne à l'environnement cible. Il peut varier en fonction de la valeur de l’argument *row_filter_option* fourni dans l’appel :<br /><br /> *row_filter_option* = 'all'<br /><br /> 'D' - opération de suppression<br /><br /> 'I' - opération d'insertion<br /><br /> 'UN' – opération de mise à jour (nouvelles valeurs)<br /><br /> *row_filter_option* = 'all update old'<br /><br /> 'D' - opération de suppression<br /><br /> 'I' - opération d'insertion<br /><br /> 'UN' – opération de mise à jour (nouvelles valeurs)<br /><br /> 'UO' – opération de mise à jour (anciennes valeurs)|  
|\<colonnes de @update_flag_list>|**bit**|Un indicateur de bit nommé en ajoutant _uflag au nom de colonne. L’indicateur est toujours défini sur NULL lorsque \__CDC_OPERATION est avait ', 'I' ou 'UO'. Lorsque \__CDC_OPERATION est un », il est défini sur 1 si la mise à jour a produit une modification dans la colonne correspondante. Sinon, il prend la valeur 0.|  
  
## <a name="remarks"></a>Notes  
 La fonction fn_all_changes_ < instance_capture > sert de wrapper pour la fonction de requête cdc.fn_cdc_get_all_changes_ < instance_capture >. La procédure stockée sys.sp_cdc_generate_wrapper sert à générer le script de création du wrapper.  
  
 Les fonctions wrapper ne sont pas créées automatiquement. Vous devez effectuer deux opérations pour créer des fonctions wrapper :  
  
1.  Exécuter la procédure stockée pour générer le script pour créer le wrapper.  
  
2.  Exécuter le script pour créer la fonction wrapper.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 Fonctions wrapper permettent aux utilisateurs d’interroger systématiquement les modifications qui se sont produites dans un intervalle lié par **datetime** valeurs au lieu de valeurs LSN. Les fonctions wrapper effectuent toutes les conversions requises entre les **datetime** valeurs et les valeurs LSN requises en interne en tant qu’arguments pour les fonctions de requête. Lorsque les fonctions wrapper sont utilisées en série pour traiter un flux de données modifiées, elles garantissent qu’aucune perte ou de données répétées condition que la convention suivante soit respectée : la @end_time valeur de l’intervalle associé à un appel est fournie en tant que le @start_time valeur pour l’intervalle associé à l’appel suivant.  
  
 L'utilisation du paramètre @closed_high_end_point lors de la création du script vous permet de générer des wrappers destinés à prendre en charge une limite supérieure fermée ou une limite supérieure ouverte sur la fenêtre de requête spécifiée. Autrement dit, vous pouvez décider si les entrées qui ont une heure de validation égale à la limite supérieure de l'intervalle d'extraction doivent être incluses dans l'intervalle. Par défaut, la limite supérieure est incluse.  
  
 Le jeu de résultats retourné par la **toutes les modifications** fonction wrapper retourne le __ $start_lsn et \_ \_$seqval des colonnes de la table de modifications en tant que colonnes \__CDC_STARTLSN et \__ CDC_SEQVAL, respectivement. Il suit ces avec uniquement les colonnes suivies qui apparaissait dans la *@column_list* paramètre lorsque le wrapper a été généré. Si *@column_list* est NULL, toutes les sources suivies, les colonnes sont renvoyées. Les colonnes sources sont suivies d’une colonne d’opération, \__CDC_OPERATION, qui est une colonne d’un ou deux caractères qui identifie l’opération.  
  
 Les indicateurs de bits sont ensuite rajoutés au jeu de résultats pour chaque colonne identifiée dans le paramètre @update_flag_list. Pour le **toutes les modifications** wrapper, les indicateurs de bits sera toujours NULL si __CDC_OPERATION est avait ', 'I' ou 'UO'. Si \__CDC_OPERATION est un ', l’indicateur a la valeur 1 ou 0, selon que l’opération de mise à jour a entraîné une modification de la colonne.  
  
 Le modèle de configuration de capture de données modifiées 'Instantiate de CDC Wrapper TVFs for Schema' illustre comment utiliser la procédure stockée sp_cdc_generate_wrapper_function pour obtenir des scripts CREATE pour toutes les fonctions wrapper pour les fonctions de requêtes définies d’un schéma. Le modèle crée ensuite ces scripts. Pour plus d’informations sur les modèles, consultez [Explorateur de modèles](../../ssms/template/template-explorer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
