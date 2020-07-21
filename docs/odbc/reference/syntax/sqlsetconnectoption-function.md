---
title: SQLSetConnectOption 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 263b15cb75fb5c0c7c1d7aa630a8da171b9765a7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301597"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption 関数
**互換性**  
 導入されたバージョン: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 ODBC 3.x で*は、odbc*2.0 関数**SQLSetConnectOption**は**SQLSetConnectAttr**に置き換えられています。 詳細については、「[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」を参照してください。  
  
> [!NOTE]
>  Odbc*2.x アプリケーションが*odbc*2.x ドライバーで*動作しているときに、ドライバーマネージャーがこの関数をマップする方法の詳細については、「[非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 アプリケーションが64ビットのオペレーティングシステムで実行される場合は、「 [ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC 3.8 で導入された属性 SQL_ASYNC_DBC_FUNCTION_ENABLE は、 **SQLSetConnectOption**ではサポートされていません。 接続ハンドルで非同期操作を使用するアプリケーションでは、 **SQLSetConnectAttr**を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
