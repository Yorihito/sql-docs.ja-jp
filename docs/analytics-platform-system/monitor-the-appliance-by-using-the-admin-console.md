---
title: 管理コンソールを使用した監視
description: 分析プラットフォームシステムの場合、管理コンソールは、アプライアンスの状態、正常性、およびパフォーマンスの情報を示す web アプリケーションです。 ユーザーは、インターネットブラウザーを使用して管理コンソールに接続します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 88e1619ce37de7c7a334ee7d915115f2deef47ef
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86941074"
---
# <a name="monitor-the-appliance-with-the-admin-console---analytics-platform-system"></a>管理コンソールを使用してアプライアンスを監視する-分析プラットフォームシステム
管理コンソールは、アプライアンスの状態、正常性、およびパフォーマンスの情報を示す SQL Server PDW web アプリケーションです。 ユーザーは、Internet Explorer を使用して管理コンソールに接続します。  
  
## <a name="about-the-admin-console"></a><a name="About"></a>管理コンソールについて  
![アプライアンス コンソールのホーム](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**アプライアンス**  
ホーム  
アプライアンスの状態の概要を簡単に説明します。  
  
健康  
各ノード内の各監視対象コンポーネントのヘルスを示すインジケーターを含むアプライアンストポロジを表示します。 ノードコンポーネントの個々のノードおよびプロパティの現在の状態を表示できます。  
  
ハードウェアおよびソフトウェアのアラートを表示します。  
  
パフォーマンス モニター  
パフォーマンスモニターのグラフを表示します。  
  
**Parallel Data Warehouse**  
ホーム  
PDW の状態の概要を説明します。  
  
セッション  
アクティブな PDW ユーザーセッションを表示します。 これは、リソースの競合を監視するのに役立ちます。  
  
クエリ  
実行中のクエリと最近完了したクエリの一覧を表示します。 関連するエラー (存在する場合) が表示されます。 には、クエリ実行プランおよびノード実行情報の詳細を表示する機能も用意されています。  
  
読み込み  
ロードプラン、PDW の読み込みの現在の状態、および関連するエラー (存在する場合) を表示します。  
  
バックアップ/復元  
PDW のバックアップおよび復元操作のログを表示します。  
  
健康  
各ノード内の各監視対象コンポーネントのヘルスを示すインジケーターを含む PDW トポロジを表示します。 ノードコンポーネントの個々のノードおよびプロパティの現在の状態を表示できます。  
  
ハードウェアおよびソフトウェアのアラートを表示します。  
  
リソース  
PDW リソースロックとその現在の状態の一覧を表示します。  
  
ストレージ  
PDW の記憶域使用率の概要を示します。  
  
パフォーマンス モニター  
PDW パフォーマンスモニターのグラフを表示します。  
 
> [!NOTE]  
> 管理コンソールの画面解像度は1024x768 です。 管理コンソールは、1280 X 1024 以上の画面解像度で最適に表示されます。  
  
## <a name="connect-to-the-admin-console"></a><a name="Connect"></a>管理コンソールに接続する  
管理コンソールに接続するには、次のものが必要です。  
  
-   Internet Explorer バージョン10以降。  
  
-   管理コンソールにアクセスするためのアクセス許可。 <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   コントロールノードクラスターの IP アドレス。  これは、SQL Server PDW 管理者から入手してください。  
  
管理コンソールに接続するには、Internet Explorer と https を使用して、コントロールノードクラスターの IP アドレスを参照します。 たとえば、コントロールノードクラスターの IP アドレスがの場合は、 `10.192.63.102` ブラウザーのアドレスバーに「」と入力し `https://10.192.63.102` ます。 最初の画面では、**ログイン**と**パスワード**が要求されます。 SQL Server 認証ログインとパスワード、または Windows 認証ログインと Windows パスワードのどちらかを指定してください。 Windows 認証ログインを使用している場合、管理コンソールは偽装を使用します。  
  
## <a name="admin-console-tasks"></a><a name="RelatedTasks"></a>管理コンソールのタスク  
管理コンソールには、次のものを監視する機能があります。  
  
|情報の種類|管理コンソールでにアクセスする方法|
|-|-|
|アプライアンスの全体的な状態|上部のメニューで [**アプライアンスの状態**] をクリックするか、[**ホーム**] をクリックします。|  
|アラート|**[アラート]** をクリックします。 詳細については、「[管理コンソールのアラートについて &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)」を参照してください。|  
|アプライアンスコンポーネントとその状態|上部のメニューで [**アプライアンスの状態**] をクリックするか、[**ホーム**] をクリックします。|  
|要求の監視 (クエリ、読み込み、バックアップ、復元など)|[**セッション**] をクリックすると、現在アクティブなセッションまたは最近のセッションが表示されます。<br /><br />[**クエリ**] をクリックすると、現在アクティブなクエリまたは最近のクエリが表示されます。 クエリに対して表示される情報には、読み込み、バックアップ、復元が含まれます。<br /><br />[**ロック**] をクリックすると、アクティブなロックが表示されます。|  
|読み込み、バックアップ、復元の追加情報を監視します。|[**読み込み**または**バックアップ/復元**] をクリックします。|  
|パフォーマンス情報|[**パフォーマンスモニター**] をクリックします。|  
  
## <a name="see-also"></a>参照  
[アプライアンス監視 &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
