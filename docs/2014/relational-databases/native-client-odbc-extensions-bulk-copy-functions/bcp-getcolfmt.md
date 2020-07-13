---
title: bcp_getcolfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: rothja
ms.author: jroth
ms.openlocfilehash: 294241eb586a70f4e0a826b1dce5d35879b3ee3e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019511"
---
# <a name="bcp_getcolfmt"></a>bcp_getcolfmt
  列形式のプロパティ値を確認するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *分野*  
 プロパティを取得する列番号です。  
  
 *プロパティ*  
 プロパティ定数のいずれかを指定します。  
  
 *pValue*  
 プロパティ値を取得するバッファーへのポインターです。  
  
 *cbValue*  
 プロパティ バッファーのバイト単位の長さです。  
  
 *pcbLen*  
 プロパティ バッファーに返されるデータの長さへのポインターです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>Remarks  
 列形式のプロパティ値については、 [bcp_setcolfmt](bcp-setcolfmt.md)のトピックを参照してください。 列形式のプロパティ値は**bcp_setcolfmt**関数を呼び出すことによって設定され、 **bcp_getcolfmt**関数は列形式のプロパティ値を検索するために使用されます。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以前のバージョンと比較して、(またはそれ以降の) サーバーコンピューターに接続するときに、動作の変更が検出される場合があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_getcolfmt による機能強化された日付と時刻のサポート  
 日付型または時刻型のプロパティと共に使用される型 `BCP_FMT_TYPE` は、 [&#40;OLE DB および ODBC&#41;の拡張された日付と時刻の型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)で指定されています。  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
