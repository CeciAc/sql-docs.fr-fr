---
title: Type de données rowset (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Rowset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Rowset
- http://schemas.microsoft.com/analysisservices/2003/engine#Rowset
- Rowset
helpviewer_keywords:
- Rowset data type
ms.assetid: a3e6e227-2d53-4530-b369-afa8b4df0a40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c4ce1858e8274e5ae964c497972b4f2b082a712
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170119"
---
# <a name="rowset-data-type-xmla"></a>Type de données Rowset (XMLA)
  Définit un type de données dérivé qui représente un [racine](../xml-elements-properties/root-element-xmla.md) élément qui retourne des données tabulaires à partir d’un [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) appel de méthode.  
  
 **Namespace** urn : schemas-microsoft-com-analysis : ensemble de lignes  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <row>...</row>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Jeu de résultats](resultset-data-type-xmla.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Ligne](../xml-elements-properties/row-element-xmla.md)|  
|Éléments dérivés|[Racine](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 XML n'autorise pas certains caractères en tant que noms d'élément et d'attribut. Pour répondre à cette contrainte d’affectation de noms, XML for Analysis (XMLA) prend en charge l’encodage tel que défini par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour les noms de colonnes qui contiennent des caractères de nom XML qui ne sont pas valides après la spécification XML 1.0, XMLA utilise les valeurs hexadécimales correspondantes pour encoder des caractères Unicode qui ne sont pas valides. Les valeurs hexadécimales sont échappés sous la forme _x*HHHH*\_, où *HHHH* représente le code de UCS-2 hexadécimal à quatre chiffres du caractère dans l’ordre premier bit le plus significatif. Par exemple, XMLA encode le nom Order Details sous la forme Order_x0020_Details remplaçant ainsi l'espace par le code hexadécimal correspondant.  
  
 L'encodage peut rendre les transformations XSL (Extensible Style Language) difficiles. Pour prendre en charge une recherche rapide des réelle, non codées noms de colonnes, ajoutez le `sql:field`attribut au schéma d’ensemble de lignes XML pour chaque colonne, comme illustré dans l’exemple suivant :  
  
```  
<xsd:element name="Order_x0020_Details" type="string" sql:field="Order Details" />  
```  
  
> [!NOTE]  
>  Attribut `sql:field` dans l'espace de noms `"urn:schemas-microsoft-com:xml-sql"`.  
  
## <a name="expressing-a-null-value"></a>Expression d'une valeur NULL  
 Il existe deux moyens d'exprimer une valeur NULL pour une colonne au sein d'une ligne :  
  
-   Un élément de colonne manquant implique que la colonne est NULL.  
  
-   L'élément de colonne peut faire appel à l'attribut `xsi:nil='true'` pour indiquer qu'il possède une valeur NULL.  
  
 Par exemple, une ligne contient une colonne unique appelée Store_Name et la valeur de cette colonne est NULL. La valeur de la colonne Store_Name peut être représentée en tant qu'élément de colonne manquant :  
  
```  
<row>  
</row>  
```  
  
 Ou elle peut aussi être représentée à l'aide de l'attribut `xsi:nil='true'` :  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
## <a name="example"></a>Exemple  
  
## <a name="xmla-rowset-for-flat-data"></a>Ensemble de lignes XMLA pour les données à deux dimensions  
 Dans le cadre des données à deux dimensions, les noms des colonnes propres à la requête sont définis dans le schéma en tant que noms d'éléments. De plus, une paire de balises `<row>` encapsule chaque ligne.  
  
 L'exemple suivant illustre le format d'ensemble de lignes XMLA pour les données à deux dimensions.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   </xsd:element>  
      <xsd:complexType name="row">  
         <xsd:choice maxOccurs="unbounded" minOccurs="0">  
            <xsd:element name="CATALOG_NAME" type="xsd:string" sql:field="CATALOG_NAME"></xsd:element>  
            <xsd:element name="DESCRIPTION" type="xsd:string" sql:field="DESCRIPTION"></xsd:element>  
            <xsd:element name="ROLES" type="xsd:string" sql:field="ROLES"></xsd:element>  
            <xsd:element name="DATE_MODIFIED" type="xsd:time" sql:field="DATE_MODIFIED"></xsd:element>  
         </xsd:choice>  
      </xsd:complexType>  
   </xsd:schema>  
   <row>  
      <CATALOG_NAME>FoodMart 2000</CATALOG_NAME>  
      <DESCRIPTION></DESCRIPTION>  
      <ROLES>All Users</ROLES>  
      <DATE_MODIFIED>3/11/2001 6:49:36 PM</DATE_MODIFIED>  
   </row>  
   ...  
</root>  
```  
  
## <a name="xmla-rowset-for-hierarchical-data"></a>Ensemble de lignes XMLA pour les données hiérarchiques  
 Certains ensembles de lignes contiennent des données hiérarchiques (ensembles de lignes imbriqués). Les ensembles de lignes retournés par les requêtes d'exploration de données sont hiérarchiques. Dans le cadre des données hiérarchiques, la structure des lignes n'est pas modifiée, mais le schéma spécifique aux données définit un sous-type d'élément qui contient les données imbriquées.  
  
 L'exemple suivant illustre le format d'ensemble de lignes XMLA pour les données hiérarchiques. Dans cet exemple, le sous-type d'élément renfermant les données imbriquées est `<NODE_DISTRIBUTION>`.  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
   xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <xsd:complexType name="row">  
         <xsd:choice maxOccurs="unbounded" minOccurs="0">  
            <xsd:sequence maxOccurs="unbounded" minOccurs="0">  
               <xsd:element name="NODE_DISTRIBUTION" sql:field="NODE_DISTRIBUTION">  
                  <xsd:complexType>  
                     <xsd:choice maxOccurs="unbounded" minOccurs="0">  
                        <xsd:element name="ATTRIBUTE_NAME" type="xsd:string" sql:field="ATTRIBUTE_NAME"></xsd:element>  
                        <xsd:element name="ATTRIBUTE_VALUE" type="xsd:string" sql:field="ATTRIBUTE_VALUE"></xsd:element>  
                        <xsd:element name="SUPPORT" type="xsd:double" sql:field="SUPPORT"></xsd:element>  
                        <xsd:element name="PROBABILITY" type="xsd:double" sql:field="PROBABILITY"></xsd:element>  
                        <xsd:element name="VARIANCE" type="xsd:double" sql:field="VARIANCE"></xsd:element>  
                        <xsd:element name="VALUETYPE" type="xsd:int" sql:field="VALUETYPE"></xsd:element>  
                     </xsd:choice>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
            <xsd:element name="MODEL_CATALOG" type="xsd:string" sql:field="MODEL_CATALOG"></xsd:element>  
            <xsd:element name="MODEL_SCHEMA" type="xsd:string" sql:field="MODEL_SCHEMA"></xsd:element>  
            <xsd:element name="MODEL_NAME" type="xsd:string" sql:field="MODEL_NAME"></xsd:element>  
            <xsd:element name="ATTRIBUTE_NAME" type="xsd:string" sql:field="ATTRIBUTE_NAME"></xsd:element>  
            <xsd:element name="NODE_NAME" type="xsd:string" sql:field="NODE_NAME"></xsd:element>  
            <xsd:element name="NODE_UNIQUE_NAME" type="xsd:string" sql:field="NODE_UNIQUE_NAME"></xsd:element>  
            <xsd:element name="NODE_TYPE" type="xsd:unsignedInt" sql:field="NODE_TYPE"></xsd:element>  
            <xsd:element name="NODE_GUID" type="xsd:string" sql:field="NODE_GUID"></xsd:element>  
            <xsd:element name="NODE_CAPTION" type="xsd:string" sql:field="NODE_CAPTION"></xsd:element>  
            <xsd:element name="CHILDREN_CARDINALITY" type="xsd:unsignedInt" sql:field="CHILDREN_CARDINALITY"></xsd:element>  
            <xsd:element name="PARENT_UNIQUE_NAME" type="xsd:string" sql:field="PARENT_UNIQUE_NAME"></xsd:element>  
            <xsd:element name="NODE_DESCRIPTION" type="xsd:string" sql:field="NODE_DESCRIPTION"></xsd:element>  
            <xsd:element name="NODE_RULE" type="xsd:string" sql:field="NODE_RULE"></xsd:element>  
            <xsd:element name="MARGINAL_RULE" type="xsd:string" sql:field="MARGINAL_RULE"></xsd:element>  
            <xsd:element name="NODE_PROBABILITY" type="xsd:double" sql:field="NODE_PROBABILITY"></xsd:element>  
            <xsd:element name="MARGINAL_PROBABILITY" type="xsd:double" sql:field="MARGINAL_PROBABILITY"></xsd:element>  
            <xsd:element name="NODE_SUPPORT" sql:type="xsd:double" sql:field="NODE_SUPPORT"></xsd:element>  
            <xsd:element name="MSOLAP_MODEL_COLUMN" sql:type="xsd:string" sql:field="MSOLAP_MODEL_COLUMN"></xsd:element>  
            <xsd:element name="MSOLAP_NODE_SCORE" sql:type="xsd:double" sql:field="MSOLAP_NODE_SCORE"></xsd:element>  
            <xsd:element name="MSOLAP_NODE_SHORT_CAPTION" sql:type="xsd:string" sql:field="MSOLAP_NODE_SHORT_CAPTION"></xsd:element>  
         </xsd:choice>  
      </xsd:complexType>  
   </xsd:schema>  
   <row>  
      <MODEL_CATALOG>FoodMart 2000</MODEL_CATALOG>  
      <MODEL_NAME>customer pattern discovery</MODEL_NAME>  
      <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
      <NODE_NAME>2147483652</NODE_NAME>  
      <NODE_UNIQUE_NAME>2147483652</NODE_UNIQUE_NAME>  
      <NODE_TYPE>2</NODE_TYPE>  
      <NODE_CAPTION>All</NODE_CAPTION>  
      <CHILDREN_CARDINALITY>8</CHILDREN_CARDINALITY>  
      <PARENT_UNIQUE_NAME>0</PARENT_UNIQUE_NAME>  
      <NODE_DESCRIPTION>All</NODE_DESCRIPTION>  
      <NODE_RULE></NODE_RULE>  
      <MARGINAL_RULE></MARGINAL_RULE>  
      <NODE_PROBABILITY>1</NODE_PROBABILITY>  
      <MARGINAL_PROBABILITY>1</MARGINAL_PROBABILITY>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>missing</ATTRIBUTE_VALUE>  
         <SUPPORT>0</SUPPORT>  
         <PROBABILITY>0</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>1</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Bronze</ATTRIBUTE_VALUE>  
         <SUPPORT>3077</SUPPORT>  
         <PROBABILITY>0.551334886221107</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Golden</ATTRIBUTE_VALUE>  
         <SUPPORT>659</SUPPORT>  
         <PROBABILITY>0.118079197276474</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Normal</ATTRIBUTE_VALUE>  
         <SUPPORT>1332</SUPPORT>  
         <PROBABILITY>0.238666905572478</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Silver</ATTRIBUTE_VALUE>  
         <SUPPORT>513</SUPPORT>  
         <PROBABILITY>9.19190109299409E-02</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_SUPPORT>5581</NODE_SUPPORT>  
      <MSOLAP_MODEL_COLUMN>Customers.Name.Member Card</MSOLAP_MODEL_COLUMN>  
      <MSOLAP_NODE_SCORE>1948.401692055</MSOLAP_NODE_SCORE>  
      <MSOLAP_NODE_SHORT_CAPTION>All</MSOLAP_NODE_SHORT_CAPTION>  
</row>  
</root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
