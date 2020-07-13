---
title: XPath データ型 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: rothja
ms.author: jroth
ms.openlocfilehash: 07fe58cee4046b78bdca0a748ea4d0c6a82dfebf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85014915"
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath のデータ型 (SQLXML 4.0)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath、および XML スキーマ (XSD) のデータ型は大きく異なります。 たとえば、XPath に整数や日付のデータ型はありませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と XSD にはこれらのデータ型が多く用意されています。 また、XSD では時間値の精度はナノ秒ですが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の精度は最大でも 1/300 秒です。 このため、あるデータ型から別のデータ型へのマッピングが常に可能であるとは限りません。 データ型の XSD データ型へのマッピングの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「[データ型の強制変換」と「sql: datatype 注釈 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)」を参照してください。  
  
 XPath には、`string`、`number`、および `boolean` の 3 つのデータ型があります。 `number` 型は、常に IEEE 754 倍精度浮動小数点数です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` データ型は、XPath に最も近いです `number` 。 ただし、`float(53)` は正確には IEEE 754 ではありません。 たとえば、非数 (NaN) も無限大も使用されません。 非数値文字列を `number` 型に変換し、0 での除算を試みると、エラーが発生します。  
  
## <a name="xpath-conversions"></a>XPath 変換  
 `OrderDetail[@UnitPrice > "10.0"]` などの XPath クエリを使用する場合は、データ型の変換を暗黙的に行うか明示的に行うかによって、クエリの意味が微妙に変わります。 このため、XPath データ型の実装方法について理解しておくことが重要です。 XPath 言語仕様である XML Path Language (XPath) バージョン 1.0 W3C 勧告では、1999年10月8日に、W3C Web サイトの「」を参照 http://www.w3.org/TR/1999/PR-xpath-19991008.html してください。  
  
 XPath の演算子は、次の 4 つのカテゴリに分けられます。  
  
-   論理演算子 (and、or)  
  
-   関係演算子 ( \<, > 、 \<=, > =)  
  
-   等価演算子 (=、!=)  
  
-   算術演算子 (+、-、*、div、mod)  
  
 各カテゴリの演算子では、それぞれ異なる方法で各自のオペランドが変換されます。 XPath の演算子では、必要に応じて各自のオペランドが暗黙的に変換されます。 算術演算子では、オペランドが `number` に変換され、数値が得られます。 論理演算子では、オペランドが `boolean` に変換され、ブール値が得られます。 関係演算子と等価演算子では、ブール値が得られます。 ただし、次の表に示すように、オペランドの変換元のデータ型に応じて、それぞれ異なる変換規則が使用されます。  
  
|オペランド|関係演算子|等値演算子|  
|-------------|-------------------------|-----------------------|  
|両方のオペランドがノード セットの場合|それぞれのセットにノードが 1 つあり、それらの `string` 値を比較した結果が TRUE の場合に限り TRUE。|同じ。|  
|一方がノード セットで、他方が `string` の場合|ノード セットにノードが 1 つあり、それを `number` に変換した値と、`string` を `number` に変換した値を比較した結果が TRUE である場合に限り TRUE。|ノード セットにノードが 1 つあり、それを `string` に変換した値と、`string` を比較した結果が TRUE である場合に限り TRUE。|  
|一方がノード セットで、他方が `number` の場合|ノード セットにノードが 1 つあり、それを `number` に変換した値と、`number` を比較した結果が TRUE である場合に限り TRUE。|同じ。|  
|一方がノード セットで、他方が `boolean` の場合|ノード セットにノードが 1 つあり、それを `boolean` に変換し、その後 `number` に変換した値と、`boolean` を `number` に変換した値を比較した結果が TRUE である場合に限り TRUE。|ノード セットにノードが 1 つあり、それを `boolean` に変換した値と、`boolean` を比較した結果が TRUE である場合に限り TRUE。|  
|どちらもノード セットでない場合|両方のオペランドを `number` に変換し比較。|両方のオペランドを共通のデータ型に変換し比較。 いずれかが `boolean` の場合は `boolean` に変換し、いずれかが `number` の場合は `number` に変換します。それ以外の場合は `string` に変換します。|  
  
> [!NOTE]  
>  XPath の関係演算子ではオペランドが常に `number` に変換されるので、`string` の比較はできません。 日付の比較を含めるため、SQL Server 2000 では XPath の仕様が変更され、関係演算子で `string` と `string`、ノード セットと `string`、または文字列値ノード セットと文字列値ノード セットが比較される場合には、`string` ではなく `number` の比較が行われるようになりました。  
  
## <a name="node-set-conversions"></a>ノード セット変換  
 ノード セット変換は常に直感的なものとは限りません。 ノード セットから `string` への変換では、セット内の先頭ノードの文字列値のみが使用されます。 ノードセットは、に変換してからに変換することによってに変換され `number` `string` `string` `number` ます。 ノード セットから `boolean` への変換では、その存在が検査されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ノード セットで位置の選択は実行されません。たとえば、XPath クエリ `Customer[3]` は 3 番目の顧客を意味しますが、このような位置の選択は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではサポートされていません。 したがって、XPath 仕様で説明されているような、ノード セットから `string`、またはノード セットから `number` への変換は実装されていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XPath 仕様で "先頭" の意味で指定されているものが "任意" の意味として扱われます。 たとえば、W3C XPath 仕様に基づき、XPath クエリは、 `Order[OrderDetail/@UnitPrice > 10.0]` **UnitPrice**が10.0 より大きい最初の**orderdetail**を持つ注文を選択します。 では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、この XPath クエリは、 **UnitPrice**が10.0 より大きい**orderdetail**を持つ注文を選択します。  
  
 `boolean` への変換では、存在検査が生成されます。このため、`Products[@Discontinued=true()]` という XPath クエリは、"Products.Discontinued = 1" という SQL 式ではなく、"Products.Discontinued is not null" という SQL 式と等価になります。 "Products.Discontinued = 1" という SQL 式と等価なクエリを作成するには、最初にノード セットを `boolean` などの、`number` 以外の型に変換します。 たとえば、「 `Products[number(@Discontinued) = true()]` 」のように入力します。  
  
 大半の演算子は、ノード セット内の 1 つ以上のノードに対して TRUE であれば TRUE となるように定義されているので、これらの演算はノード セットが空の場合は常に FALSE となります。 したがって、A が空の場合、`A = B` と `A != B` は両方とも FALSE になり、`not(A=B)` と `not(A!=B)` は TRUE になります。  
  
 通常、列にマップされる属性や要素は、データベース内でその列の値が `null` でない場合に存在します。 行にマップされる要素は、子が存在する場合に存在します。  
  
> [!NOTE]  
>  `is-constant` で注釈される要素は常に存在します。 したがって、XPath 述語を `is-constant` 要素に使用することはできません。  
  
 ノード セットが `string` または `number` に変換される場合、注釈付きスキーマにその XDR 型が指定されているかどうかが調べられ、見つかった場合はその型によって必要な変換が判別されます。  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>XDR データ型から XPath データ型へのマッピング  
 ノードの XPath データ型は、次の表に示すように、スキーマ内の XDR データ型から派生します (この**ノードは、説明的な**目的で使用されます)。  
  
|XDR データ型|同等の<br /><br /> XPath データ型|使用される SQL Server 変換|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|N/A|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number、int、float,i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8|number|CONVERT(float(53), EmployeeID)|  
|id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (XDR データ型 fixed14.4 に相当する XPath のデータ型はありません)|CONVERT(money, EmployeeID)|  
|date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|時間<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 日付と時刻の変換は、値がデータ型またはを使用してデータベースに格納されているかどうかにかかわらず機能するように設計されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` `string` ます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` データ型はを使用せず、 `timezone` XML データ型よりも精度が低いことに注意して `time` ください。 `timezone` 型または追加の有効桁数を含めるには、`string` 型を使って [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータを格納します。  
  
 ノードが XDR データ型から XPath データ型に変換される場合は、1 つの XPath データ型から別の XPath データ型へ、追加の変換が必要になることがあります。 たとえば、次の XPath クエリを考えてみます。  
  
```  
(@m + 3) = 4  
```  
  
 @mが `fixed14.4` xdr データ型の場合、xdr データ型から XPath データ型への変換は、以下を使用して行われます。  
  
```  
CONVERT(money, m)  
```  
  
 この変換で、ノード `m` は `fixed14.4` から `money` に変換されます。 しかし、値 3 を加算するには追加の変換が必要になります。  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 この XPath 式は、次のように評価されます。  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 次の表に示すように、これは、リテラルや複合式など、他の XPath 式に適用される変換と同じです。  
  
||||||  
|-|-|-|-|-|  
||X が不明|X が `string`|X が `number`|X が `boolean`|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN (X) > 0|X != 0|-|  
  
## <a name="examples"></a>例  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. XPath クエリ内のデータ型を変換する  
 注釈付き XSD スキーマに対して指定された次の XPath クエリでは、 **EmployeeID**属性値が E-1 のすべての**Employee**ノードが選択されます。ここで、"e-" は、注釈を使用して指定されたプレフィックスです `sql:id-prefix` 。  
  
 `Employee[@EmployeeID="E-1"]`  
  
 クエリ内の述語は、次の SQL 式と等価です。  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 **Employeeid**は XSD スキーマのデータ型の値 (、、、など) の1つであるため `id` `idref` `idrefs` `nmtoken` `nmtokens` 、前**EmployeeID**に `string` 説明した変換規則を使用して、employeeid を XPath データ型に変換します。  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 文字列に "E-" プレフィックスが追加され、結果が `N'E-1'` と比較されます。  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. XPath クエリ内で複数のデータ型変換を実行する  
 注釈付き XSD スキーマに対して指定される XPath クエリ `OrderDetail[@UnitPrice * @OrderQty > 98]` を考えてみます。  
  
 この XPath クエリは、述語を満たすすべての要素を返し **\<OrderDetail>** `@UnitPrice * @OrderQty > 98` ます。 注釈付きスキーマのデータ型で、 **UnitPrice**に注釈が付けられている場合 `fixed14.4` 、この述語は SQL 式に相当します。  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 XPath クエリ内の値を変換するとき、最初の変換では、XDR データ型を XPath データ型に変換します。 前の表で説明したように、 **UnitPrice**の XSD データ型はであり、 `fixed14.4` 最初に使用される変換です。  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 算術演算子ではオペランドが `number` XPath データ型に変換されるので、1 つの XPath データ型から別の XPath データ型への追加変換が適用され、値は `float(53)` に変換されます。`float(53)` に近い XPath のデータ型は `number` です。  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 **Orderqty**属性に XSD データ型が含まれていない場合、 **orderqty**は `number` 1 回の変換で XPath データ型に変換されます。  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 同様に、値 98 は `number` XPath データ型に変換されます。  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  スキーマで使用されている XSD データ型がデータベース内の基になるデータ型と互換性がない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または XPath データ型の変換が不可能な場合は、に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よってエラーが返されることがあります。 たとえば、 **employeeid**属性に注釈が付いている場合、 `id-prefix` `Employee[@EmployeeID=1]` **employeeid**には注釈があり、 `id-prefix` に変換することはできないため、XPath ではエラーが生成され `number` ます。  
  
  
