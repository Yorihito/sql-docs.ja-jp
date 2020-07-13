---
title: ステートメントハンドルを割り当てる |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: rothja
ms.author: jroth
ms.openlocfilehash: fac0802b474f38f6a6c314dd727fa335d14598d1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85018700"
---
# <a name="allocating-a-statement-handle"></a>ステートメント ハンドルの割り当て
  アプリケーションでステートメントを実行する前に、ステートメント ハンドルを割り当てる必要があります。 これを行うには、 *Handletype*パラメーターを SQL_HANDLE_STMT に設定し、 *InputHandle*をポイントするように**SQLAllocHandle**を呼び出します。  
  
 ステートメント属性は、ステートメント ハンドルの特徴を表します。 ブックマークやカーソルを使用してサンプル ステートメント属性を取り込み、ステートメントの結果セットと共に使用することができます。 ステートメント属性は[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)で設定され、それらの現在の設定は[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)を使用して取得されます。 アプリケーションでステートメント属性を設定する必要はありません。すべてのステートメント属性には既定値があり、一部の属性は、ドライバー固有の属性になっています。  
  
 複数の ODBC ステートメント オプションと接続オプションを使用する場合は、注意が必要です。 *Foption*を SQL_ATTR_LOGIN_TIMEOUT に設定して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出すと、接続の確立を待機している間にアプリケーションが接続試行を待機する時間を制御します (0 は無限の待機を指定します)。 応答時間が遅いサイトでは、この値を高く設定して、接続の完了までに十分な時間を与えることができます。 ただしこの間隔は、ドライバーが接続できない場合に、妥当な時間内にユーザーに応答できる程度に低く抑える必要があります。  
  
 *Foption*を SQL_ATTR_QUERY_TIMEOUT に設定して**SQLSetStmtAttr**を呼び出すと、クエリのタイムアウト間隔が設定され、実行時間の長いクエリからサーバーとユーザーを保護できます。  
  
 *Foption*を SQL_ATTR_MAX_LENGTH に設定して**SQLSetStmtAttr**を呼び出すと、個々のステートメントが取得できる**テキスト**と**画像**データの量が制限されます。 *Foption*を SQL_ATTR_MAX_ROWS に設定して**SQLSetStmtAttr**を呼び出すと、すべてのアプリケーションが必要とする場合に、行セットが最初の*n*行に制限されます。 SQL_ATTR_MAX_ROWS を設定すると、ドライバーがサーバーに対して SET ROWCOUNT ステートメントを実行することになります。 これ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、トリガーや更新プログラムを含むすべてのステートメントに影響します。  
  
 上記のオプションを設定するときは注意が必要です。 SQL_ATTR_MAX_LENGTH と SQL_ATTR_MAX_ROWS の場合、接続ハンドルのすべてのステートメント ハンドルが同じ設定になるようにすることをお勧めします。 ドライバーが、あるステートメント ハンドルから、これらのオプションに異なる値を持つ別のステートメント ハンドルに切り替える場合、適切な SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを生成して、設定を変更する必要があります。 ユーザー SQL ステートメントには、バッチ内では先頭に含めなければならないステートメントを含めることができるので、ドライバーはユーザー SQL ステートメントと同じバッチ内にこれらのステートメントを配置することはできません。 ドライバーは SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを別のバッチで送信する必要があります。その結果、サーバーに対する追加のラウンドトリップが自動的に生成されます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;クエリの実行](executing-queries-odbc.md)  
  
  
