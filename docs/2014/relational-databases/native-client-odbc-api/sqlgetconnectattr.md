---
title: SQLGetConnectAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: rothja
ms.author: jroth
ms.openlocfilehash: f82a0fb71103e811b36280f9722c160791023e44
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022366"
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ドライバー固有の接続属性が定義されます。 一部の属性はで使用でき `SQLGetConnectAttr` ます。関数は、現在の設定をレポートするために使用されます。 これらの属性について報告される値は、接続が確立されるか、または[SQLSetConnectAttr](sqlsetconnectattr.md)を使用して属性が設定されるまでは保証されません。  
  
 ここでは、読み取り専用の属性を示します。 Native Client ODBC ドライバー固有のその他の接続属性の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQLSetConnectAttr](sqlsetconnectattr.md)」を参照してください。  
  
## <a name="sql_copt_ss_connection_dead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 SQL_COPT_SS_CONNECTION_DEAD 属性では、サーバーへの接続状態が報告されます。 ドライバーは、接続の現在の状態をネットワークにクエリします。  
  
> [!NOTE]  
>  標準の ODBC 接続属性 SQL_ATTR_CONNECTION_DEAD は、接続の最新の状態を返します。 これは現在の接続状態と異なる場合があります。  
  
|値|説明|  
|-----------|-----------------|  
|SQL_CD_TRUE|サーバーへの接続が失われました。|  
|SQL_CD_FALSE|接続が開かれており、ステートメントの処理に使用できます。|  
  
## <a name="sql_copt_ss_client_connection_id"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 SQL_COPT_SS_CLIENT_CONNECTION_ID 属性は、クライアント接続 ID を取得します。この ID を使用すると、次の情報を検索できます。  
  
-   XEvent ログの診断情報 (有効な場合)。  
  
-   接続リング バッファーの接続エラー情報。  
  
-   データ アクセスのトレース ログの診断情報 (有効な場合)。  
  
 詳細については、「[拡張イベントログの診断情報へのアクセス](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)」を参照してください。  
  
|値|説明|  
|-----------|-----------------|  
|SQL_ERROR|接続に失敗しました。|  
|SQL_SUCCESS|接続に成功しました。 クライアント接続 ID は出力バッファーで見つかります。|  
  
## <a name="sql_copt_ss_perf_data"></a>SQL_COPT_SS_PERF_DATA  
 SQL_COPT_SS_PERF_DATA 属性は、現在のドライバーのパフォーマンス統計情報を保持する SQLPERF 構造体へのポインターを返します。 `SQLGetConnectAttr`パフォーマンスログが有効になっていない場合、は NULL を返します。 SQLPERF 構造体内の統計情報がドライバーで動的に更新されることはありません。 `SQLGetConnectAttr`パフォーマンス統計を更新する必要があるたびに、を呼び出します。  
  
|値|説明|  
|-----------|-----------------|  
|NULL|パフォーマンスのログ記録が無効です。|  
|その他の値|SQLPERF 構造体へのポインター。|  
  
## <a name="sql_copt_ss_perf_query"></a>SQL_COPT_SS_PERF_QUERY  
 SQL_COPT_SS_PERF_QUERY 属性は、実行時間の長いクエリのログ記録が有効の場合に TRUE を返します。 クエリのログ記録が無効の場合は FALSE を返します。  
  
## <a name="sql_copt_ss_user_data"></a>SQL_COPT_SS_USER_DATA  
 SQL_COPT_SS_USER_DATA 属性は、ユーザー データ ポインターを取得します。 ユーザー データはクライアントのメモリに格納され、接続ごとに記録されます。 ユーザー データ ポインターが設定されていない場合、SQL_UD_NOTSET という NULL ポインターが返されます。  
  
|値|説明|  
|-----------|-----------------|  
|SQL_UD_NOTSET|ユーザー データ ポインターが設定されていません。|  
|その他の値|ユーザー データへのポインターです。|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>SQLGetConnectAttr によるサービス プリンシパル名 (SPN) のサポート  
 SQLGetConnectAttr を使用すると、SQL_COPT_SS_SERVER_SPN、SQL_COPT_SS_FAILOVER_PARTNER_SPN、SQL_COPT_SS_MUTUALLY_AUTHENTICATED、および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD の新しい接続属性の値を照会できます。 (SQLGetConnectOption を使用してこれらの値を照会することもできます)。  
  
 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD は、Windows 認証を使用する、開いている接続でのみ使用できます。  
  
 SQL_COPT_SS_SERVER_SPN または SQL_COPT_SS_FAILOVER_PARTNER が設定されていない場合は、既定値 (空の文字列) が返されます。  
  
 Spn の詳細については、「[クライアント接続 &#40;ODBC&#41;のサービスプリンシパル名 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLGetConnectAttr 関数](https://go.microsoft.com/fwlink/?LinkId=59347)   
 [ODBC API の実装の詳細](odbc-api-implementation-details.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)   
 [SET ANSI_NULLS &#40;Transact-sql&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [SET ANSI_PADDING &#40;Transact-sql&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
