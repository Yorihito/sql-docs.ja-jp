---
title: テーブルおよび列への XSD 要素と属性の既定のマッピング (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XSD schemas [SQLXML], mapping attributes and elements
- mapping schema [SQLXML], default mapping
- element mapping [SQLXML], default mapping
- element mapping [SQLXML]
- table mapping [SQLXML]
- annotated XSD schemas, mapping attributes and elements
- table/view mapping [SQLXML]
- column mapping [SQLXML]
- attribute mapping [SQLXML], default mapping
- default schema mapping
- table mapping [SQLXML], default mapping
- testing XPath query against schema
- xml data type [SQL Server], SQLXML
- table/view mapping [SQLXML], default mapping
- element/attribute mapping [SQLXML]
ms.assetid: 9a18e92a-6cfb-4a14-993a-663a95aabb63
author: rothja
ms.author: jroth
ms.openlocfilehash: 96df35ea1b8d87aa8718a29b51c07ab5a427efc7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055163"
---
# <a name="default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a>テーブルおよび列への XSD 要素および属性の既定のマッピング (SQLXML 4.0)
  既定では、XSD 注釈付きスキーマの複合型の要素は、指定されたデータベース内の同じ名前のテーブル (ビュー) にマップされ、単純型の要素または属性は、テーブル内の同じ名前の列にマップされます。  
  
## <a name="examples"></a>例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-specifying-default-mapping"></a>A. 既定のマッピングを指定する  
 この例では、XSD スキーマで注釈は指定されていません。 **\<Person.Contact>** 要素は複合型であるため、既定で AdventureWorks データベースの Person. Contact テーブルにマップされます。 要素のすべての属性 (ContactID、FirstName、LastName) **\<Person.Contact>** は単純型で、既定では、Person. Contact テーブル内の同じ名前の列にマップされます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  type="xsd:string" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 MySchema.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 MySchema.xml を保存したディレクトリに MySchemaT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchema.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (MySchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 次に結果セットの一部を示します。  
  
```  
<?xml version="1.0" encoding="UTF-8" ?>  
<ROOT>  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong"/>  
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel"/>  
   ...  
</ROOT>  
```  
  
### <a name="b-mapping-an-xml-element-to-a-database-column"></a>B. XML 要素をデータベース列にマップする  
 この例では、注釈が使用されず、既定のマッピングが行われます。 **\<Person.Contact>** 要素は複合型であり、データベース内の同じ名前のテーブルにマップされます。 要素 **\<FirstName>** および **\<LastName>** **EmployeeID**属性は単純型であるため、同じ名前の列にマップされます。 前の例との唯一の違いは、FirstName フィールドと LastName フィールドのマップに要素を使用する点です。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="FirstName" type="xsd:string" />   
        <xsd:element name="LastName" type="xsd:string" />   
      </xsd:sequence>  
      <xsd:attribute name="ContactID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 MySchemaElements.xml として保存します。  
  
2.  次のテンプレート (MySchemaElementsT.xml) を作成し、前の手順と同じディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaElements.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマに指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaElements.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 次に結果セットの一部を示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1">  
    <FirstName>Gustavo</FirstName>  
    <LastName>Achong</LastName>  
  </Person.Contact>  
   ...  
</ROOT>  
```  
  
### <a name="c-mapping-an-xml-element-to-an-xml-data-type-column"></a>C. XML 要素を XML データ型の列にマップする  
 この例では、注釈が使用されず、既定のマッピングが行われます。 **\<Production.ProductModel>** 要素は複合型であり、データベース内の同じ名前のテーブルにマップされます。 **Productmodelid**属性は単純型であるため、同じ名前の列にマップされます。 このと前の例の唯一の違いは、要素が型を使用して **\<Instructions>** データ型を使用する列にマッピングされていることです `xml` `xsd:anyType` 。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Instructions" type="xsd:anyType" />   
      </xsd:sequence>  
      <xsd:attribute name="ProductModelID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 `xml` データ型は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入されました。  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 MySchemaXmlAnyElements.xml として保存します。  
  
2.  次のテンプレート (MySchemaXmlAnyElementsT.xml) を作成し、前の手順と同じディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaXmlAnyElements.xml">  
            /Production.ProductModel[@ProductModelID=7]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマに指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaXmlAnyElements.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 次に結果セットの一部を示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductModel ProductModelID="7">  
    <Instructions>  
      <root xmlns="http:  
//schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstru  
ctions">  
...  
      </root>  
    <Instructions>  
  </Production.ProductModel>  
</ROOT>  
```  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0&#41;&#40;注釈付きスキーマのセキュリティに関する考慮事項](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [XML データ &#40;SQL Server&#41;](../xml/xml-data-sql-server.md)   
 [SQLXML 4.0 での xml データ型のサポート](../sqlxml/xml-data-type-support-in-sqlxml-4-0.md)  
  
  
