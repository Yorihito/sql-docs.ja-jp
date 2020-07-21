---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3fe50863656db9faf60613c0ff9f4de7a9d18875
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019716"
---
# <a name="bcp_collen"></a>bcp_collen
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対する現在の一括コピー用のプログラム変数にデータ長を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *cbData*  
 プログラム変数内のデータ長です。長さのインジケーターやターミネータの長さは含まれません。 *Cbdata*を SQL_NULL_DATA に設定すると、サーバーにコピーされるすべての行に列の NULL 値が格納されます。 また、SQL_VARLEN_DATA に設定すると、文字列ターミネータや他の方法を使用してコピーするデータ長が決定されます。 長さのインジケーターとターミネータの両方を指定した場合、システムはコピーするデータ量が少なくなる方法を使用します。  
  
 *idxServerCol*  
 テーブル内にある、データのコピー先となる列の序数位置です。 最初の列は 1 です。 列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>Remarks  
 **Bcp_collen**関数を使用すると、bcp_sendrow でデータをにコピーするときに、特定の列のプログラム変数のデータ長を変更でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [bcp_sendrow](bcp-sendrow.md)  
  
 初期状態では、データの長さは[bcp_bind](bcp-bind.md)が呼び出されるときに決定されます。 **Bcp_sendrow**の呼び出し間でデータ長が変化し、長さのプレフィックスやターミネータが使用されていない場合は、 **bcp_collen**を呼び出して長さをリセットできます。 次に**bcp_sendrow**を呼び出すと、 **bcp_collen**の呼び出しによって設定された長さが使用されます。  
  
 データ長を変更するテーブルの列ごとに**bcp_collen**を呼び出す必要があります。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
