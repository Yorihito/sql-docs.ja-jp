---
title: 'データ型の強制変換と sql: datatype 注釈 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: rothja
ms.author: jroth
ms.openlocfilehash: 61da7fafe60ef31246a436e21a5110c121d094e2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84996411"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>データ型の強制型変換と sql:datatype 注釈 (SQLXML 4.0)
  XSD スキーマでは、`xsd:type` 属性を使用して、要素または属性の XSD データ型を指定できます。 XSD スキーマを使用したデータベースからのデータの抽出では、指定されているデータ型を使用して、データが書式設定されます。  
  
 スキーマでは、XSD 型を指定する他に、`sql:datatype` 注釈を使用して、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定することもできます。 これらの `xsd:type` および `sql:datatype` 属性では、XSD データ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の間のマッピングが制御されます。  
  
## <a name="xsdtype-attribute"></a>xsd:type 属性  
 `xsd:type` 属性を使用すると、列にマップする属性や要素の XML データ型を指定できます。 `xsd:type` はサーバーから返されるドキュメントだけでなく、実行される XPath クエリにも影響します。 `xsd:type` を含むマッピング スキーマに対して XPath クエリを実行すると、XPath でクエリが処理されるときに、指定されたデータ型が使用されます。 XPath の使用方法の詳細については `xsd:type` 、「 [&#41;の Xpath データ型への XSD データ型のマッピング &#40;SQLXML 4.0 ](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)」を参照してください。  
  
 返されるドキュメントでは、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型は文字列表記に変換されます。 また、データ型によっては追加の変換が必要です。 次の表は、さまざまな `xsd:type` 値とそれに対して使用される変換の一覧です。  
  
|XSD データ型|SQL Server の変換|  
|-------------------|---------------------------|  
|Boolean|CONVERT(bit, COLUMN)|  
|Date|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|時間|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|その他すべて|追加の変換はありません。|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から、`xsd:type` で指定される XML データ型と互換性のない値が返される場合もあります。たとえば、"XYZ" は `decimal` データ型に変換できない値であり、-100,000 は `UnsignedShort` XSD 型に変換するとデータ型の範囲を超える値となるためです。 互換性のない型を変換しようとすると、無効な XML ドキュメントが生成されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーになる可能性があります。  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>SQL Server データ型から XSD データ型へのマッピング  
 次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型から XSD データ型への明確なマッピングです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型がわかっている場合は、XSD スキーマで指定できる、対応する XSD 型をこの表で確認してください。  
  
|SQL Server のデータ型|XSD データ型|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a>sql:datatype 注釈  
 `sql:datatype` 注釈を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定できます。この注釈は、次の場合に指定する必要があります。  
  
-   `dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XSD `dateTime` 、 `date` 、または型の列 `time` に一括読み込みを行う場合。 この場合、`sql:datatype="dateTime"` を使って [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のデータ型を指定する必要があります。 この規則はアップデートグラムにも当てはまります。  
  
-   型の列に一括読み込みを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` 行い、XSD 値は、中かっこ ({および}) を含む GUID です。 `sql:datatype="uniqueidentifier"` を指定すると、値が列に挿入される前に中かっこが削除されます。 `sql:datatype` を指定しないと、値が中かっこ付きのまま送信され、挿入または更新は失敗します。  
  
-   XML データ型 `base64Binary` は、さまざまな [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型 (`binary`、`image`、または `varbinary`) にマップされます。 XML データ型 `base64Binary` を特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にマップするには、`sql:datatype` 注釈を使用します。 この注釈では、属性のマップ先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を明示的に指定できます。 これは、データをデータベースに格納する場合に便利で、 `sql:datatype` 注釈を指定することにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を明示的に識別できます。  
  
 一般に、スキーマでは `sql:datatype` を指定することをお勧めします。  
  
## <a name="examples"></a>例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。  
  
### <a name="a-specifying-xsdtype"></a>A. xsd:type を指定する  
 この例では、スキーマ内で `date` 属性を使って指定した XSD `xsd:type` 型が、結果の XML ドキュメントにどのように影響するかを示します。 このスキーマでは、AdventureWorks データベース内の Sales.SalesOrderHeader テーブルの XML ビューが提供されます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 この XSD スキーマには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から日付値を返す 3 つの属性が含まれています。 それぞれの属性は次のとおりです。  
  
-   `xsd:type=date` **Orderdate**属性にを指定します。 orderdate 属性に対してによって返される値の日付部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が表示されます。 **OrderDate**  
  
-   `xsd:type=time` **ShipDate**属性でを指定します。 ShipDate 属性に対してによって返される値の時刻部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が表示されます。 **ShipDate**  
  
-   では、DueDate 属性にが指定されていません `xsd:type` 。によって返されるのと同じ**DueDate**値 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が表示されます。  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 xsdType.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 xsdType.xml を保存したディレクトリに xsdTypeT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (xsdType.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 次に結果セットの一部を示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 これは、これと同等の XDR スキーマです。  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>B. sql:datatype を使用して SQL データ型を指定する  
 実際のサンプルについては、「 [XML 一括読み込みの例 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)」を参照してください。 この例では、"{" および "}" を含む GUID 値の一括読み込みが行われます。 この例のスキーマでは、`sql:datatype` を指定し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を `uniqueidentifier` として識別します。 この例は、どのような場合にスキーマで `sql:datatype` を指定する必要があるかを示すものです。  
  
  
