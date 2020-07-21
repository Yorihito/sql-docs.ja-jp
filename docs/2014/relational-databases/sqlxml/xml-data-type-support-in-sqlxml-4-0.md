---
title: SQLXML 4.0 | での xml データ型のサポートMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
author: rothja
ms.author: jroth
ms.openlocfilehash: 7c7338500b68c157d5b555e29cf3a88bea3513c5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85009294"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>SQLXML 4.0 での xml データ型のサポート
  以降 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を使用した XML 型のデータがサポートされてい `xml` ます。 ここでは、SQLXML 4.0 で `xml` データ型のインスタンスがどのように認識されるかと、それらがどのようにサポートされるかについて情報を提供します。  
  
## <a name="working-with-xml-data-types"></a>xml データ型の使用  
 `xml` データ型の列を実装する SQL テーブルの処理方法の理解に役立つように、次の例が用意されています。  
  
|タスク|例|トピック|  
|----------|-------------|-----------|  
|`xml` 列を XML ビューにマップし、格納する方法|"XML 要素を XML データ型の列にマップする"|[テーブルおよび列への XSD 要素と属性の既定のマッピング &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|アップデートグラムで `xml` 列にデータを挿入する方法|"XML データ型列にデータを挿入する"|[XML アップデートグラムを使用したデータの挿入 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|`xml` 列への XML データの一括読み込み|"xml データ型の列に一括読み込みを行う"|[XML 一括読み込みの例 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>ガイドラインと制限  
  
-   **\<xsd:any>** データ型を含む列にマップすることはできません `xml` 。 この場合、SQLXML では `sql:overflow-field` 注釈を使用して対処できます。 または、`xml` データ型のフィールドに `xsd:anyType` の要素としてマップすることもできます。 この方法は、上の表の例 "XML 要素を XML データ型の列にマップする" に示されています。  
  
-   `xml` データ型の列のコンテンツに XPath クエリを実行することはできません。  
  
-   `xml` や `sql:relationship` など、`sql:key-fields` データ型の列がサポートまたは許可されていない注釈でこのデータ型の列を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーが発生し、発生したエラーは SQLXML 4.0 を実装する中間層コンポーネントでトラップされません。 これは、SQLXML で SQL 型の情報が必要とされないためです。 この動作は、BLOB やバイナリ型などその他のデータ型に対する SQLXML の動作と同様です。  
  
-   `xml` 列のマッピングは、XSD スキーマでのみサポートされています。 XDR スキーマでは、`xml` 列のマッピングはサポートされていません。  
  
-   SQLXML 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で提供される XML 解析サポートに依存しています。 `xml` 列は、型指定された XML または型指定されない XML のいずれかとしてマップできます。 どちらの場合も、SQLXML 4.0 で入力 XML は検証されません。  入力 XML が有効でないか、適切な形式でない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQLXML にそのことがレポートされ、サーバーによって返された関連エラー情報がある場合はユーザーに伝達されます。  
  
-   SQLXML 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で提供される DTD の制限付きサポートに依存しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では `xml` データ型のデータの内部 DTD が許可されるので、既定値の設定や、エンティティ参照の拡張コンテンツへの置き換えに使用できます。 SQLXML では、サーバーに XML データが "そのまま" (内部 DTD を含めて) 渡されます。 ここで、サード パーティのツールを使用して DTD を XML スキーマ (XSD) ドキュメントに変換し、データをインライン XSD スキーマと共にデータベースに読み込むことができます。  
  
-   SQLXML 4.0 では、の動作に基づいて、XML 宣言の処理命令 (たとえば、) は保持されません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 代わりに、XML 宣言は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML パーサーに対するディレクティブとして扱われ、データが `xml` データ型に変換された後は、属性 (バージョン、エンコーディング、およびスタンドアロン) は失われます。 XML データは内部的に UCS-2 として保存されます。 XML インスタンス内のその他すべての処理命令は保持されます。これらは `xml` 列で許可され、SQLXML でサポートされます。  
  
## <a name="see-also"></a>参照  
 [XML データ &#40;SQL Server&#41;](../xml/xml-data-sql-server.md)  
  
  
