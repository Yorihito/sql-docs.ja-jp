---
title: 'Sql: マップトを使用した、結果の XML ドキュメントからのスキーマ要素の除外 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: rothja
ms.author: jroth
ms.openlocfilehash: ceb1d222131c14810d3d71bdd8faf13509f97614
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055142"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a>sql:mapped を使用した、結果の XML ドキュメントからのスキーマ要素の除外 (SQLXML 4.0)
  既定のマッピングでは、XSD スキーマのすべての要素と属性が、データベースのテーブルまたはビューと列にマップされます。 XSD スキーマで、データベース テーブル (ビュー) または列にマップせず、XML に表示しない要素を作成する場合は、`sql:mapped` 注釈を指定できます。  
  
 `sql:mapped` 注釈は、データベースに格納されていないデータがスキーマにあり、そのスキーマを変更できない場合や、そのスキーマが他のソースからの XML の検証に使用されている場合に特に便利です。 `sql:mapped` 注釈は、マップされない要素と属性が XML ドキュメントに表示されないという点で、`sql:is-constant` と異なります。  
  
 `sql:mapped` 注釈はブール値 (0 = false、1 = true) をとります。 指定できる値は 0、1、true、false です。  
  
## <a name="examples"></a>例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. sql:mapped 注釈を指定する  
 他のソースからの XSD スキーマがあるとします。 この XSD スキーマは **\<Person.Contact>** 、 **ContactID**、 **FirstName**、 **LastName**、および**ホームアドレス**属性を持つ要素で構成されています。  
  
 この XSD スキーマを AdventureWorks データベースの Person. Contact テーブルにマップする場合、 `sql:mapped` employee テーブルには従業員の自宅の住所が格納されないため、[ホーム**アドレス**] 属性にはが指定されています。 この結果、マッピング スキーマに対して Xpath クエリを指定すると、属性はデータベースにマップされず、結果の XML ドキュメント内に返されません。  
  
 スキーマの残りの部分に対しては、既定のマッピングが適用されます。 **\<Person.Contact>** 要素は person. contact テーブルにマップされ、すべての属性は、person. contact テーブル内の同じ名前の列にマップされます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 sql-mapped.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 sql-mapped.xml を保存したディレクトリに sql-mappedT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (MySchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 結果セットは次のようになります。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 マッピング スキーマで `sql:mapped` 属性に 0 を指定しているので、ContactID と FirstName、Lastname は存在しますが、HomeAddress は存在しないことに注意してください。  
  
## <a name="see-also"></a>参照  
 [テーブルおよび列への XSD 要素と属性の既定のマッピング &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
