---
title: Analysis Services のログ操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa1db060-95dc-4198-8aeb-cffdda44b140
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00554c9e56bebe12a5e63c9d50e4a2fa59149599
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543824"
---
# <a name="log-operations-in-analysis-services"></a>Analysis Services でのログ操作
  Analysis Services インスタンスは、サーバーの通知、エラー、および警告を msmdsrv.exe ファイルに記録します。インストールするインスタンスごとに1つです。 管理者は、ルーチンのイベントと異常なイベントのどちらの情報を得る場合でも、このログを参照します。 最近のリリースにおいては、ログ記録が機能拡張され、さらに多くの情報が含まれるようになりました。 ログ レコードには、製品のバージョンおよびエディション情報だけでなく、プロセッサ、メモリ、接続、およびブロック イベントも含まれるようになりました。 [ログ記録の機能強化](https://support.microsoft.com/kb/2965035)に関するページで、全体的な変更の一覧を確認できます。  
  
 組み込みのログ記録機能以外にも、多くの管理者および開発者が、Analysis Services コミュニティが提供する **ASTrace**などのツールを使用して、サーバー操作に関するデータを収集しています。 ダウンロードのリンクについては、「 [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) 」 (Microsoft SQL Server コミュニティ サンプル: Analysis Services) を参照してください。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [ログの場所と種類](#bkmk_location)  
  
-   [ログファイルの構成設定に関する一般的な情報](#bkmk_general)  
  
-   [MSMDSRV サービス ログ ファイル](#bkmk_msmdsrv)  
  
-   [クエリログ](#bkmk_querylog)  
  
-   [ミニダンプ (mdmp) ファイル](#bkmk_mdmp)  
  
-   [ヒントとベスト プラクティス](#bkmk_tips)  
  
> [!NOTE]  
>  ログ記録の情報をお探しの場合、処理およびクエリの実行パスを示す操作のトレースに関心を持たれるかもしれません。 アドホックかつ持続的なトレース(キューブ アクセスの監査など) のためのトレース オブジェクト、および Flight Recorder、SQL Server Profiler、および xEvents を最適に使用する方法に関する推奨事項は、このページ (「 [Analysis Services インスタンスの監視](monitor-an-analysis-services-instance.md)」) のリンクから確認できます。  
  
##  <a name="location-and-types-of-logs"></a><a name="bkmk_location"></a>ログの場所と種類  
 Analysis Services では、次に示すログが提供されています。  
  
|ファイルの名前または場所|種類|使用目的|既定でオン|  
|---------------------------|----------|--------------|-------------------|  
|Msmdsrv.log|エラー ログ|ルーチン監視と基本的なトラブルシューティング|はい|  
|リレーショナル データベースの OlapQueryLog テーブル|クエリ ログ|[使用法の最適化] ウィザードでの入力の収集|いいえ|  
|SQLDmp \<guid> ファイル|クラッシュと例外|高度なトラブルシューティング|いいえ|  
  
 このトピックで説明されていない追加の情報リソースについては、 [マイクロソフト サポートからの初期データ コレクションに関するヒントのページ](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)を参照することをお勧めします。  
  
##  <a name="general-information-on-log-file-configuration-settings"></a><a name="bkmk_general"></a> ログ ファイルの構成設定に関する一般情報  
 各ログのセクションは msmdsrv.ini サーバー構成ファイル内にあります。このファイルは \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config フォルダーにあります。 ファイルを編集する手順については、「 [Analysis Services でのサーバープロパティの構成](../server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 可能であれば、Management Studio の [サーバーのプロパティ] ページにあるログ記録のプロパティを設定することをお勧めします。 ただし、場合によっては、管理ツールに表示されていない設定を構成するため、msmdsrv.ini ファイルを直接編集する必要があります。  
  
 ![ログ設定を示した構成ファイルのセクション](../media/ssas-logfilesettings.png "ログ設定を示した構成ファイルのセクション")  
  
##  <a name="msmdsrv-service-log-file"></a><a name="bkmk_msmdsrv"></a>MSMDSRV.EXE サービスログファイル  
 Analysis Services は、サーバーの操作のログを msmdsrv.log ファイルにインスタンスごとに記録します。このログ ファイルの場所は \program files\Microsoft SQL Server\\<instance\>\Olap\Log です。  
  
 このログ ファイルは、サービスを再起動するたびに空になります。 以前のリリースでは、ログ ファイルが使用できなくなるほど肥大化する事態を避けるためだけに、管理者がサービスを再起動してログ ファイルをフラッシュするということも行われていました。 これはもう不要です。 SQL Server 2012 SP2 以降で導入された構成設定では、ログ ファイルとその履歴のサイズを制御できます。  
  
-   `MaxFileSizeMB` は、ログ ファイルの最大サイズを MB 単位で指定します。 既定値は 256 です。 置き換える有効な値は正の整数である必要があります。 Analysis Services は、`MaxFileSizeMB` に達すると、現在のファイルの名前を msmdsrv{現在のタイムスタンプ}.log ファイルに変更し、新しい msmdsrv.log ファイルの使用を開始します。  
  
-   `MaxNumberFiles` は、古いログ ファイルの保有期間を指定します。 既定値は 0 (無効) です。 ログ ファイルのバージョンを維持するには、正の整数に変更します。 Analysis Services は、`MaxNumberFiles` に達すると、名前のタイムスタンプが最も古いものからファイルを削除します。  
  
 これらの設定を使用するには、以下を実行します。  
  
1.  msmdsrv.ini をメモ帳で開きます。  
  
2.  次の 2 行をコピーします。  
  
    ```  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    ```  
  
3.  この 2 行を、msmdsrv.ini の Log セクション (msmdsrv.log のファイル名の下にある) に貼り付けます。 両方の設定を手動で追加する必要があります。 msmdsrv.ini ファイル内にプレースホルダーはありません。  
  
     変更された構成ファイルは、次のようになります。  
  
    ```  
    <Log>  
    <File>msmdsrv.log</File>  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    <FileBufferSize>0</FileBufferSize>  
  
    ```  
  
4.  与えられた値が希望と異なる場合は、値を編集します。  
  
5.  ファイルを保存します。  
  
6.  サービスを再起動します。  
  
##  <a name="query-logs"></a><a name="bkmk_querylog"></a> クエリ ログ  
 クエリ ログの名称には若干誤りがあります。というのは、クエリ ログではユーザーの MDX クエリや DAX クエリの操作をログに記録しないためです。 代わりに、クエリ ログでは、Analysis Services によって生成されるクエリに関するデータを収集します。その後、このデータが [使用法に基づく最適化] ウィザードのデータ入力として使用されます。 クエリ ログに収集されたデータは直接分析するためのものではありません。 具体的には、データセットは、データセットのパスがクエリに含まれることを示す 0 または 1 のビット配列で記述されます。 ここでも、このデータはウィザード向けのものです。  
  
 クエリの監視とトラブルシューティングのため、多くの開発者および管理者は、クエリを監視するためにコミュニティ ツール **ASTrace**を使用します。 また、SQL Server Profiler、xEvents、または Analysis Services トレースも使用できます。 トレース関連のリンクについては、「 [Analysis Services インスタンスの監視](monitor-an-analysis-services-instance.md) 」を参照してください。  
  
 クエリ ログを使用する場合 [使用法に基づく最適化] ウィザードを含むクエリ パフォーマンス チューニングの練習の一部として、クエリ ログを有効にすることをお勧めします。 機能を有効にして、機能をサポートするデータ構造を作成し、Analysis Services がログの検索と作成に使用するプロパティを設定するまでは、クエリ ログは存在しません。  
  
 クエリ ログを有効にするには、次の手順に従います。  
  
1.  クエリ ログを格納する SQL Server リレーショナル データベースを作成します。  
  
2.  Analysis Services のサービス アカウントに、データベースに対する十分なアクセス許可を付与します。 アカウントには、テーブルの作成、テーブルへの書き込み、テーブルからの読み取りの権限が必要です。  
  
3.  SQL Server Management Studio で**Analysis Services**プロパティの全般] を右クリックし  |  **Properties**  |  **General**、[ **createquerylogtable** ] を [true] に設定します。  
  
4.  (省略可能) クエリを異なるレートでサンプリングする場合、またはテーブルに異なる名前を使用する場合は、 **QueryLogSampling** または **QueryLogTableName** を変更します。  
  
 サンプリングの要件を満たすだけの十分な MDX クエリを実行するまでクエリ ログ テーブルは作成されません。 たとえば、10 の既定値を維持する場合は、テーブルが作成されるまでに少なくとも 10 個のクエリを実行する必要があります。  
  
 クエリ ログの設定は、サーバー全体に適用します。 指定した設定は、このサーバーで実行されているすべてのデータベースで使用されます。  
  
 ![Management Studio でのクエリ ログの設定](../media/ssas-querylogsettings.png "Management Studio でのクエリ ログの設定")  
  
 構成設定を指定したら、MDX クエリを複数回実行します。 サンプリングを 10 に設定している場合は、クエリを 11 回実行します。テーブルが作成されていることを確認します。 Management Studio で、リレーショナル データベース エンジンに接続し、データベース フォルダーを開きます。 **Tables** フォルダーを開き、 **OlapQueryLog** が存在していることを確認します。 テーブルがすぐに表示されない場合は、フォルダーの情報を更新して内容への変更を取得します。  
  
 クエリ ログが [使用法に基づく最適化] ウィザードに十分なデータを蓄積できるようにします。 クエリのボリュームが循環的である場合は、代表的なデータのセットを得るのに十分なトラフィック量をキャプチャします。 ウィザードの実行方法の説明については、「 [使用法に基づく最適化ウィザード](https://msdn.microsoft.com/library/ms189706.aspx) 」を参照してください。  
  
 クエリ ログの構成については、「 [Analysis Services クエリ ログの構成](https://technet.microsoft.com/library/Cc917676) 」を参照してください。 記事は非常に古いものですが、クエリ ログの構成は最近のリリースでは変更されておらず、含まれている情報は引き続き適用されます。  
  
##  <a name="mini-dump-mdmp-files"></a><a name="bkmk_mdmp"></a> ミニ ダンプ (.mdmp) ファイル  
 ダンプ ファイルでは、異例なイベントを分析するために使用されるデータをキャプチャします。 Analysis Services は、サーバーのクラッシュ、例外、およびいくつかの構成エラーに対応してミニ ダンプ (.mdmp) を自動的に生成します。 機能が有効であっても、クラッシュ レポートは自動的に送信されません。  
  
 クラッシュ レポートは、Msmdsrv.ini ファイルの「Exception (例外)」セクションで構成します。 これらの設定は、メモリ ダンプ ファイルの生成を制御します。 次のスニペットは、既定値を示しています。  
  
```  
<Exception>  
<CreateAndSendCrashReports>1</CreateAndSendCrashReports>  
<CrashReportsFolder/>  
<SQLDumperFlagsOn>0x0</SQLDumperFlagsOn>  
<SQLDumperFlagsOff>0x0</SQLDumperFlagsOff>  
<MiniDumpFlagsOn>0x0</MiniDumpFlagsOn>  
<MiniDumpFlagsOff>0x0</MiniDumpFlagsOff>  
<MinidumpErrorList>0xC1000000, 0xC1000001, 0xC102003F, 0xC1360054, 0xC1360055</MinidumpErrorList>  
<ExceptionHandlingMode>0</ExceptionHandlingMode>  
<CriticalErrorHandling>1</CriticalErrorHandling>  
<MaxExceptions>500</MaxExceptions>  
<MaxDuplicateDumps>1</MaxDuplicateDumps>  
</Exception>  
```  
  
 **クラッシュ レポートの構成**  
  
 特に Microsoft サポートから指示がない限り、ほとんどの管理者は既定の設定を使用します。 このサポート技術情報「 [メモリ ダンプ ファイルを生成するように Analysis Services を構成する方法](https://support.microsoft.com/kb/919711)」は古いものですが、ダンプ ファイルの構成手順として今も使用されています。  
  
 最も変更される可能性が高い構成設定は、メモリ ダンプ ファイルを生成するかどうかの指定に使用する `CreateAndSendCrashReports` の設定です。  
  
|値|説明|  
|-----------|-----------------|  
|0|メモリ ダンプ ファイルをオフにします。 「Exception (例外)」セクションの他のすべての設定は無視されます。|  
|1|(既定) メモリ ダンプ ファイルを有効にしますが送信しません。|  
|2|有効にするとともに、エラー レポートを Microsoft に自動的に送信します。|  
  
 `CrashReportsFolder` はダンプ ファイルの場所です。 既定では、.mdmp ファイルと関連付けられているログ レコードは \Olap\Log フォルダー内にあります。  
  
 `SQLDumperFlagsOn` は完全ダンプの生成に使用されます。 既定では、完全ダンプは無効です。 このプロパティは `0x34` に設定します。  
  
 次のリンクに詳しい背景情報があります。  
  
-   [ミニダンプを使用する SQL Server について詳しく知る](https://blogs.msdn.com/b/sqlcat/archive/2009/09/11/looking-deeper-into-sql-server-using-minidumps.aspx)  
  
-   [ユーザー モードのダンプ ファイルを作成する方法](https://support.microsoft.com/kb/931673)  
  
-   [Sqldumper.exe ユーティリティを使用して SQL Server にダンプ ファイルを生成する方法](https://support.microsoft.com/kb/917825)  
  
##  <a name="tips-and-best-practices"></a><a name="bkmk_tips"></a>ヒントとベストプラクティス  
 このセクションは、この記事全体で説明したヒントの要約です。  
  
-   msmdsrv log ファイルのサイズと数を制御するには、msmdsrv.log ファイルを構成します。 既定では設定が無効になっているため、必ずインストール後の手順として設定を追加してください。 このトピックの [MSMDSRV サービス ログ ファイル](#bkmk_msmdsrv) を参照してください。  
  
-   サーバーの操作に関する情報の取得に使用するリソースについて知るには、マイクロソフト カスタマー サポートから [最初のデータの収集に関するブログの投稿](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)を確認します。  
  
-   キューブのクエリを実行している人を確認するには、クエリ ログではなく ASTrace2012 を使用します。 通常、クエリ ログは、[使用法に基づく最適化] ウィザードへの入力に使用され、クエリ ログでキャプチャしたデータは読み取りや解釈が簡単ではありません。 ASTrace2012 は、クエリ操作のキャプチャに広く使われているコミュニティ ツールです。 「 [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/)」 (Microsoft SQL Server コミュニティ サンプル: Analysis Services) を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンス管理](analysis-services-instance-management.md)   
 [SQL Server プロファイラーを使用した Analysis Services の監視の概要](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)   
 [Analysis Services のサーバーのプロパティの構成](../server-properties/server-properties-in-analysis-services.md)  
  
  
