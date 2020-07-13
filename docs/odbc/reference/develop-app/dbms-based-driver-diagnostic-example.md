---
title: DBMS ベースのドライバー診断の例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117f43548d2b57233dea6f7423e6bad67b6233b0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304353"
---
# <a name="dbms-based-driver-diagnostic-example"></a>DBMS ベースのドライバー診断の例
DBMS ベースのドライバーは、DBMS に要求を送信し、ドライバーマネージャーを使用してアプリケーションに情報を返します。 ドライバーはドライバーマネージャーとのインターフェイスを持つコンポーネントであるため、 **SQLGetDiagRec**の引数を書式設定して返します。  
  
 たとえば、SQL/Services を使用している場合、Microsoft driver for Oracle Rdb で無効なカーソル名が検出された場合は、 **SQLGetDiagRec**から次の値が返される可能性があります。  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 ドライバーでエラーが発生したため、ベンダー ([Microsoft]) とドライバー ([ODBC Rdb ドライバー]) の診断メッセージにプレフィックスが追加されました。  
  
 DBMS が EMPLOYEE テーブルを見つけることができなかった場合、ドライバーは**SQLGetDiagRec**から次の値を書式設定して返します。  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 データソースでエラーが発生したため、ドライバーによってデータソース識別子 ([Rdb]) のプレフィックスが診断メッセージに追加されました。 ドライバーは、データソースとの通信を行うコンポーネントであったので、そのベンダー ([Microsoft]) と識別子 ([ODBC Rdb ドライバー]) のプレフィックスが診断メッセージに追加されました。
