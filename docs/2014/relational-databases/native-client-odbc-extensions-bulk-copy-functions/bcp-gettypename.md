---
title: bcp_gettypename |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: rothja
ms.author: jroth
ms.openlocfilehash: 0341d9ba11cd66fdbfb72a05521028098c56c400
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019439"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
  指定された BCP 型トークンの SQL 型名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *token*  
 BCP 型トークンを示す値です。  
  
 *分野*  
 要求されたトークンが max 型かどうかを示します。  
  
## <a name="returns"></a>戻り値  
 BCP 型に対応する SQL 型名を含む文字列を返します。 無効な BCP 型が指定されると、空文字列を返します。  
  
## <a name="remarks"></a>Remarks  
 BCP 型トークンは、sqlncli.h ヘッダー ファイルと sqlncli11.lib ライブラリで定義されています。  
  
 次の表では、指定できる BCP 型、それらの BCP 型が max 型かどうか、および予想される出力を示しています。  
  
|BCP 型名|MaxType|出力|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|接続前/接続後|**decimal**|  
|`SQLNUMERIC`|接続前/接続後|**numeric**|  
|`SQLINT1`|接続前/接続後|**tinyint**|  
|`SQLINT2`|接続前/接続後|**smallint**|  
|`SQLINT4`|接続前/接続後|**int**|  
|`SQLMONEY`|接続前/接続後|**money**|  
|`SQLFLT8`|接続前/接続後|**float**|  
|`SQLDATETIME`|接続前/接続後|**datetime**|  
|`SQLBITN`|接続前/接続後|**bit-null**|  
|`SQLBIT`|接続前/接続後|**bit**|  
|`SQLBIGCHAR`|いいえ|**char**|  
|`SQLCHARACTER`|いいえ|**char**|  
|`SQLBIGVARCHAR`|いいえ|**varchar**|  
|`SQLVARCHAR`|いいえ|**varchar**|  
|`SQLTEXT`|接続前/接続後|**text**|  
|`SQLBIGBINARY`|いいえ|**[バイナリ]**|  
|`SQLBINARY`|いいえ|**Binary**|  
|`SQLBIGVARBINARY`|いいえ|**可変長**|  
|`SQLVARBINARY`|いいえ|**可変長**|  
|`SQLIMAGE`|接続前/接続後|**イメージ**|  
|`SQLINTN`|接続前/接続後|**int-null**|  
|`SQLDATETIMN`|接続前/接続後|**datetime-null**|  
|`SQLMONEYN`|接続前/接続後|**money-null**|  
|`SQLFLTN`|接続前/接続後|**float-null**|  
|`SQLAOPSUM`|接続前/接続後|**求め**|  
|`SQLAOPAVG`|接続前/接続後|**Avg**|  
|`SQLAOPCNT`|接続前/接続後|**Count**|  
|`SQLAOPMIN`|接続前/接続後|**」**|  
|`SQLAOPMAX`|接続前/接続後|**制限**|  
|`SQLDATETIM4`|接続前/接続後|**smalldatetime**|  
|`SQLMONEY4`|接続前/接続後|**Smallmoney**|  
|`SQLFLT4`|接続前/接続後|**本当の**|  
|`SQLUNIQUEID`|接続前/接続後|**uniqueidentifier**|  
|`SQLNCHAR`|いいえ|**Nchar**|  
|`SQLNVARCHAR`|いいえ|**Nvarchar**|  
|`SQLNTEXT`|接続前/接続後|**Ntext**|  
|`SQLVARIANT`|接続前/接続後|**sql_variant**|  
|`SQLINT8`|接続前/接続後|**Bigint**|  
|`SQLCHARACTER`|はい|**varchar(max)**|  
|`SQLBIGCHAR`|はい|**varchar(max)**|  
|`SQLBIGVARCHAR`|はい|**varchar(max)**|  
|`SQLVARCHAR`|はい|**varchar(max)**|  
|`SQLBINARY`|はい|**varbinary(max)**|  
|`SQLBIGBINARY`|はい|**varbinary(max)**|  
|`SQLBIGVARBINARY`|はい|**varbinary(max)**|  
|`SQLVARBINARY`|はい|**varbinary(max)**|  
|`SQLNCHAR`|はい|**nvarchar(max)**|  
|`SQLNVARCHAR`|はい|**nvarchar(max)**|  
|`SQLXML`|はい|**Xml**|  
|`SQLUDT`|接続前/接続後|**Udt**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename による機能強化された日付と時刻のサポート  
 日付/時刻型のトークンパラメーター値については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付と時刻の型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。 返される値は、対応する行の "ファイル ストレージ型" 列に示されています。  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
