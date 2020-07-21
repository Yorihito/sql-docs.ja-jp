---
title: アップデートグラムでの注釈付きマッピングスキーマの指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4594940cd2db9eabaf5011d10e56dcab1ac39159
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015042"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a>アップデートグラムでの注釈付きマッピング スキーマの指定 (SQLXML 4.0)
  ここでは、アップデートグラムで指定したマッピング スキーマ (XSD または XDR) が、更新の処理にどのように使用されるかについて説明します。 アップデートグラムでは、アップデートグラムの要素と属性をのテーブルと列にマップするときに使用する、注釈付きマッピングスキーマの名前を指定でき [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。 アップデートグラムでマッピング スキーマを指定する場合、アップデートグラムで指定する要素と属性名は、マッピング スキーマ内の要素と属性にマップされる必要があります。  
  
 マッピングスキーマを指定するには、 `mapping-schema` 要素の属性を使用し **\<sync>** ます。 次の例では、単純なマッピング スキーマを使用するアップデートグラムと、より複雑なスキーマを使用するアップデートグラムの 2 つのアップデートグラムを示します。  
  
> [!NOTE]  
>  このドキュメントは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるテンプレートとマッピング スキーマについて理解していることを前提としています。 詳細については、「[注釈付き XSD スキーマの概要 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」を参照してください。 XDR を使用するレガシアプリケーションでは、 [SQLXML 4.0&#41;では、注釈付き Xdr スキーマ &#40;非推奨](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)とされています。  
  
## <a name="dealing-with-data-types"></a>データ型の扱い  
 スキーマで、、、 `image` `binary` またはのいずれかのデータ型を指定し、 `varbinary` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] xml データ型を指定しない場合 `sql:datatype` 、アップデートグラムでは xml データ型がであると想定され `binary base 64` ます。 データが `bin.base` 型の場合は、明示的に型 (`dt:type=bin.base` または `type="xsd:hexBinary"`) を指定する必要があります。  
  
 `dateTime`、`date`、または `time` の XSD データ型を指定する場合は、`sql:datatype="dateTime"` を使用して、対応する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型も指定する必要があります。  
  
 型のパラメーターを処理する場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` 、 `sql:datatype="money"` マッピングスキーマの適切なノードに明示的にを指定する必要があります。  
  
## <a name="examples"></a>例  
 次の例を使用して実際のサンプルを作成するには、 [SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)を満たす必要があります。  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a>A. 単純なマッピング スキーマを使用するアップデートグラムを作成する  
 次の XSD スキーマ (SampleSchema.xml) は、 **\<Customer>** 要素を Sales. Customer テーブルにマップするマッピングスキーマです。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 次のアップデートグラムでは、Sales.Customer テーブルにレコードを挿入します。ここでは上のマッピング スキーマに従って、このデータをテーブルに適切にマップします。 アップデートグラムでは、 **\<Customer>** スキーマで定義されているのと同じ要素名が使用されていることに注意してください。 アップデートグラムで特定のスキーマを指定するときには、これが必須となります。  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 SampleUpdateSchema.xml として保存します。  
  
2.  下のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 SampleUpdateSchema.xml を保存したディレクトリに SampleUpdategram.xml として保存します。  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleUpdateSchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 これは、これと同等の XDR スキーマです。  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a>B. マッピング スキーマに指定されている親子リレーションシップを使用して、レコードを挿入する  
 スキーマ要素は関連付けることができます。 要素は、 **\<sql:relationship>** スキーマ要素間の親子リレーションシップを指定します。 この情報は、主キー/外部キーのリレーションシップがある対応するテーブルを更新するときに使用されます。  
  
 次のマッピングスキーマ (SampleSchema.xml) は、との2つの要素で構成されてい **\<Order>** **\<OD>** ます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 次のアップデートグラムでは、この XSD スキーマを使用して、注文43860の新しい注文明細レコード ( **\<OD>** ブロック内の要素) を追加し **\<after>** ます。 `mapping-schema` 属性は、アップデートグラム内でマッピング スキーマを指定するために使用されます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 SampleUpdateSchema.xml として保存します。  
  
2.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 SampleUpdateSchema.xml を保存したディレクトリに SampleUpdategram.xml として保存します。  
  
     マッピング スキーマ (SampleUpdateSchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 これは、これと同等の XDR スキーマです。  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a>C. XSD スキーマで指定されている親子リレーションシップと inverse 注釈を使用して、レコードを挿入する  
 この例では、XSD で指定される親子リレーションシップがアップデートグラム ロジックでどのように使用され、更新が処理されるかと、`inverse` 注釈がどのように使用されるかを示します。 注釈の詳細につい `inverse` ては、「 [sql: relationship での sql: 逆属性の指定 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)」を参照してください。  
  
 この例では、次のテーブルが**tempdb**データベースにあることを前提としています。  
  
-   `Cust (CustomerID, CompanyName)`。ここでは `CustomerID` は主キーです。  
  
-   `Ord (OrderID, CustomerID)`。ここでは `CustomerID` は外部キーで、`CustomerID` テーブル内の `Cust` 主キーを参照します。  
  
 このアップデートグラムでは次の XSD スキーマを使用して、Cust および Ord テーブルにレコードを挿入します。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 この例の XSD スキーマには、 **\<Customer>** 要素と要素があり、 **\<Order>** 2 つの要素間の親子リレーションシップを指定します。 **\<Order>** 親要素として、および子要素としてを識別し **\<Customer>** ます。  
  
 アップデートグラム処理ロジックでは、親子リレーションシップに関する情報に基づいて、レコードがテーブルに挿入される順序が決定されます。 この例では、アップデートグラムロジックはまず、Ord テーブルにレコードを挿入しようとし (は親であるため **\<Order>** )、Cust テーブルにレコードを挿入しようとします (は子であるため) **\<Customer>** 。 しかし、データベース テーブル スキーマに含まれる主キー/外部キーの情報に対して、この挿入操作はデータベースの外部キー違反となるため、挿入は失敗します。  
  
 アップデートグラムロジックに対して、更新操作中に親子関係を反転するように指示するに `inverse` は、要素に注釈を指定し **\<relationship>** ます。 こうすると、最初に Cust テーブル、次に Ord テーブルにレコードが追加され、操作は成功します。  
  
 次のアップデートグラムでは、指定された XSD スキーマを使用して、Ord テーブルに注文 (OrderID=2)、Cust テーブルに顧客 (CustomerID='AAAAA') を挿入します。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  次のテーブルを**tempdb**データベースに作成します。  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 SampleUpdateSchema.xml として保存します。  
  
3.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 SampleUpdateSchema.xml を保存したディレクトリに SampleUpdategram.xml として保存します。  
  
     マッピング スキーマ (SampleUpdateSchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
