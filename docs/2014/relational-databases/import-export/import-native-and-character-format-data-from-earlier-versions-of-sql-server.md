---
title: 以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 274c984d6ecec8af8f5bea27496450a45fc2f1df
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85026804"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a>以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、 **bcp** を使用すると、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] からネイティブ形式データおよび文字形式データを **-V** スイッチを指定してインポートすることができます。 **-V** スイッチを使用すると、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は指定された以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータ型を使用し、データ ファイル形式はその以前のバージョンのものと同じになります。  
  
 データ ファイルに以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンを指定するには、 **-V** スイッチと次のいずれかの修飾子を使用します。  
  
|SQL Server のバージョン|Qualifier|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## <a name="interpretation-of-data-types"></a>データ型について  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、いくつかの新しいデータ型がサポートされるようになりました。 以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンに新しいデータ型をインポートする場合は、古い **bcp** クライアントで読み取ることが可能な形式でそのデータ型を格納する必要があります。 次の表では、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との互換性を維持するために、新しいデータ型がどのように変換されるかをまとめています。  
  
|SQL Server 2005 の新しいデータ型|バージョン 6*x*の互換性のあるデータ型|バージョン 70 の互換性のあるデータ型|バージョン 80 の互換性のあるデータ型|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|XML|`ntext`|`ntext`|`ntext`|  
|UDT<sup>1</sup>|`image`|`image`|`image`|  
  
 \*この型はネイティブでサポートされています。  
  
 <sup>1</sup> UDT は、ユーザー定義型を示します。  
  
## <a name="exporting-using--v-80"></a>-V 80 を使用したエクスポート  
 **-V80**スイッチを使用してデータを一括エクスポートする場合、、、 `nvarchar(max)` `varchar(max)` `varbinary(max)` 、XML、およびネイティブモードの UDT データは、、、およびデータのように4バイトのプレフィックスを使用して格納され `text` `image` `ntext` ます。これは、以降のバージョンの既定の8バイトのプレフィックス [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではなく、、、などです。  
  
## <a name="copying-date-values"></a>日付値のコピー  
 **bcp** は ODBC 一括コピー API を使用します。 したがって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **bcp** に日付値をインポートするには、ODBC の日付形式 (*yyyy-mm-dd hh:mm:ss*[ *.f...* ]) を使用します。  
  
 **Bcp**コマンドは、およびの値に対して ODBC の既定の形式を使用して、文字形式のデータファイルをエクスポートし `datetime` `smalldatetime` ます。 たとえば、日付 `12 Aug 1998` が含まれた `datetime` 型の列は、文字列 `1998-08-12 00:00:00.000` としてデータ ファイルに一括コピーされます。  
  
> [!IMPORTANT]  
>  Bcp を使用してフィールドにデータをインポートする場合は、 `smalldatetime` 秒の値が00.000 であることを確認してください。そうしないと、操作は失敗します。 **bcp** `smalldatetime` データ型には、最も近い "分" までの値のみが保持されます。 この場合、BULK INSERT および INSERT ... SELECT * FROM OPENROWSET(BULK...) は失敗しませんが、秒の値は切り捨てられます。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
 **一括インポートまたは一括エクスポートのデータ形式を使用するには**  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a>参照  
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [SQL Server データベース エンジンの旧バージョンとの互換性](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [CAST および CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
