---
title: SQLGetEnvAttr, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d09182bc39d99a99f3d03957e296c91101b0fe5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538134"
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetEnvAttr** retourne le paramètre actuel d’un attribut de l’environnement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironmentHandle*  
 [Entrée] Handle d’environnement.  
  
 *Attribute*  
 [Entrée] Attribut à récupérer.  
  
 *ValuePtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner la valeur actuelle de l’attribut spécifié par *attribut*.  
  
 Si *ValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée  *ValuePtr*.  
  
 *BufferLength*  
 [Entrée] Si *ValuePtr* pointe vers une chaîne de caractères, cet argument doit être la longueur de \* *ValuePtr*. Si \* *ValuePtr* est un entier, *BufferLength* est ignoré. Si  *\*ValuePtr* est une chaîne Unicode (lors de l’appel **SQLGetEnvAttrW**), la *BufferLength* argument doit être un nombre pair. Si la valeur d’attribut n’est pas une chaîne de caractères, *BufferLength* n’est pas utilisé.  
  
 *StringLengthPtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner le nombre total d’octets (sans le caractère de fin de la valeur null) disponibles à renvoyer dans  *\*ValuePtr*. Si *ValuePtr* est un pointeur null, aucune longueur n’est retournée. Si la valeur d’attribut est une chaîne de caractères et le nombre d’octets à retourner est supérieur ou égal à *BufferLength*, les données dans \* *ValuePtr* est tronqué à  *BufferLength* moins la longueur d’un caractère du caractère nul de terminaison et se terminant par null par le pilote.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetEnvAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_ENV et un *gérer* de *EnvironmentHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetEnvAttr** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|Les données retournées dans \* *ValuePtr* a été tronquée pour être *BufferLength* moins le caractère de fin de la valeur null. La longueur de la valeur de chaîne non tronqué est retournée dans **StringLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQL_ATTR_ODBC_VERSION** n’a pas encore été définie par le biais de **SQLSetEnvAttr**. Vous n’avez pas besoin de définir **SQL_ATTR_ODBC_VERSION** explicitement si vous utilisez **SQLAllocHandleStd**.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY092|Identificateur d’option/attribut non valide|La valeur spécifiée pour l’argument *attribut* n’était pas valide pour la version d’ODBC pris en charge par le pilote.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La valeur spécifiée pour l’argument *attribut* a un attribut d’environnement ODBC valide pour la version d’ODBC pris en charge par le pilote, mais n’était pas pris en charge par le pilote.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote correspondant à la *EnvironmentHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Pour obtenir la liste d’attributs, consultez [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Il n’existe aucun attribut d’environnement spécifique au pilote. Si *attribut* spécifie un attribut qui retourne une chaîne, *ValuePtr* doit être un pointeur vers une mémoire tampon dans lequel retourner la chaîne. La longueur maximale de la chaîne, y compris l’octet de caractère nul de terminaison, sera *BufferLength* octets.  
  
 **SQLGetEnvAttr** peut être appelée à tout moment entre l’allocation et la libération d’un handle d’environnement. Tous les attributs d’environnement a été définies par l’application pour l’environnement persistent jusqu'à **SQLFreeHandle** est appelée sur le *EnvironmentHandle* avec un *HandleType*de SQL_HANDLE_ENV. Plus d’un handle d’environnement peut être alloué simultanément dans ODBC 3 *.x*. Un attribut d’environnement dans un environnement n’est pas affecté quand un autre environnement a été alloué.  
  
> [!NOTE]
>  L’attribut d’environnement SQL_ATTR_OUTPUT_NTS est pris en charge par les applications conformes aux normes. Lorsque **SQLGetEnvAttr** est appelée, le 3 ODBC *.x* Gestionnaire de pilotes retourne toujours SQL_TRUE pour cet attribut. SQL_ATTR_OUTPUT_NTS peut être définie avec SQL_TRUE uniquement par un appel à **SQLSetEnvAttr**.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retourner le paramètre d’un attribut de connexion|[SQLGetConnectAttr, fonction](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Retourner le paramètre d’un attribut d’instruction|[SQLGetStmtAttr, fonction](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Définition d’un attribut de connexion|[SQLSetConnectAttr, fonction](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Définition d’un attribut d’environnement|[SQLSetEnvAttr, fonction](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Définition d’un attribut d’instruction|[SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
