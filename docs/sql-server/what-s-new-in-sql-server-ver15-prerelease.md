---
title: SQL Server 2019 CTP アナウンス アーカイブ | Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 191c5f2e603821a5bb9d85aa89a630c71800e660
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424423"
---
# <a name="sql-server-2019-ctp-announcement-archive"></a>SQL Server 2019 CTP アナウンス アーカイブ

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (CTP) リリースの機能に関するアナウンス アーカイブを提供します。 これは履歴の目的で提供されていますが、運用環境または最新のプレリリース バージョンの [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] には適用されません。

この記事は、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の運用環境へのリリース時に削除される予定です。

最新の情報については、[SQL Server 2019 の新機能](what-s-new-in-sql-server-ver15.md)に関するページを参照してください。

## <a name="ctp-31-june-2019"></a>CTP 3.1 2019 年 6 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:---|:---|
| `mssqlctl` コマンドの変更 | `mssqlctl cluster` コマンドの名前が、`mssqlctl bdc` に変更されました。 詳しくは、[`mssqlctl` のリファレンス](../big-data-cluster/reference-azdata.md)に関する記事をご覧ください。 |
|`mssqlsctl` の新しい状態コマンド|`mssqlctl` に、既存の監視コマンドを補完する新しいコマンドが追加されます。 これらは、クラスター管理ポータルに代わるものです。クラスター管理ポータルはこのリリースで削除されます。|
| Spark コンピューティング プール | ストレージをスケールアップする必要なしに、追加ノードを作成して Spark のコンピューティング能力を増強します。 さらに、Spark に使われない記憶域プールのノードを開始することができます。 Spark と記憶域は切り離されています。 詳しくは、「[Configure storage without spark (Spark なしで記憶域を構成する)](../big-data-cluster/deployment-custom-configuration.md#sparkstorage)」をご覧ください。 |
| MSSQL Spark コネクタ | データ プール外部テーブルの読み取り/書き込みのサポート。 以前のリリースでは、MASTER インスタンス テーブルの読み取り/書き込みだけがサポートされていました。 詳しくは、「[How to read and write to SQL Server from Spark using the MSSQL Spark Connector (MSSQL Spark コネクタを使用して Spark から SQL Server の読み取りと書き込みを行う方法)](../big-data-cluster/spark-mssql-connector.md)」をご覧ください。 |
| MLeap を使用する機械学習 | [Spark で MLeap 機械学習モデルをトレーニングし、Java 言語拡張機能を使用して SQL Server でスコアリングします](../big-data-cluster/spark-create-machine-learning-model.md)。 |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:---|:---|
|暗号化された列のインデックス付け|ランダム化された暗号化およびエンクレーブ対応のキーを使用して暗号化された列のインデックスを作成し、リッチなクエリのパフォーマンスを向上させます (`LIKE` と比較演算子を使用)。 「[セキュリティで保護されたエンクレーブが設定された Always Encrypted](../relational-databases/security/encryption/always-encrypted-enclaves.md)」をご覧ください。
|セットアップ時に `MIN` と `MAX` のサーバー メモリ値を設定する |セットアップの間に、サーバー メモリの値を設定できます。 **推奨される**オプションである[サーバー メモリのサーバー構成オプション](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually)を選択した後、既定値、計算された推奨値、または独自の値の手動指定を使用します。
|新しいグラフ関数 - `SHORTEST_PATH` | `MATCH` 内で `SHORTEST_PATH` を使用し、グラフ内の任意の 2 ノード間の最短パスを検索するか、任意の長さのトラバーサルを実行します。|
|グラフ データベースのパーティション テーブルとインデックス|パーティション テーブルとパーティション インデックスのデータは、グラフ データベース内の複数のファイル グループに分散できるように、複数の単位に分割されます。 |
|-インデックスの新しいオプション - `OPTIMIZE_FOR_SEQUENTIAL_KEY`|インデックスへの高コンカレンシーの挿入のスループット向上に役立つ、データベース エンジン内での最適化を有効にします。 このオプションは、最終ページ挿入の競合が起きやすいインデックスを対象としています。これは、一般に、ID 列、シーケンス、または日付/時刻列などの連続したキーを持つインデックスでよく見られます。 詳しくは、「[CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys)」をご覧ください。|
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>Linux 上の SQL Server

| 新機能または更新 | 詳細 |
|:-----|:-----|
| tempdb の強化機能 | 既定では、Linux 上に SQL Server を新しくインストールすると、論理コアの数に基づいて複数の tempdb データ ファイルが作成されます(最大で 8 個のデータ ファイル)。 これは、マイナー バージョンまたはメジャー バージョンのインプレース アップグレードには適用されません。 各 tempdb ファイルは 8 MB で、64 MB まで自動拡張します。 この動作は、Windows への SQL Server の既定のインストールに似ています。 |
| &nbsp; | &nbsp; |

## <a name="ctp-30-may-2019"></a>CTP 3.0 2019 年 5 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:---|:---|
| **mssqlctl** の更新 | 複数の **mssqlctl** [コマンドとパラメーターが更新されました](../big-data-cluster/reference-mssqlctl.md)。 これには、コントローラーのユーザー名とエンドポイントをターゲットにするようになった **mssqlctl login** コマンドの更新も含まれています。 |
| ストレージの機能強化 | ログとデータのさまざまなストレージ構成のサポート。 また、ビッグ データ クラスターへの永続ボリューム要求の数が削減されました。 |
| 複数のコンピューティング プール インスタンス | 複数のコンピューティング プール インスタンスのサポート。 |
| 新しいプールの動作と機能 | コンピューティング プールは、既定で **ROUND_ROBIN** 配布内​​のストレージ プールおよびデータ プールの操作にのみ使用されるようになりました。 データ プールで新しい **REPLICATED** 分布の種類が使用できるようになりました。これは、同じデータがすべてのデータ プール インスタンスに存在することを意味します。 |
| 外部テーブルの機能強化 | HADOOP データ ソースの種類の外部テーブルで、最大サイズ 1 MB の行の読み取りがサポートされるようになりました。 外部テーブル (ODBC、記憶域プール、データ プール) で、SQL Server テーブルと同じ幅の行がサポートされるようになりました。 |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:---|:---|
|SQL Server 言語拡張機能 - [Java 言語拡張機能](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|[Microsoft SQL Server 用の Microsoft Extensibility SDK for Java](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) がオープン ソース化され、[GitHub で入手可能](https://github.com/microsoft/sql-server-language-extensions)になりました。|
|外部言語を登録する|新しい DDL `CREATE EXTERNAL LANGUAGE` では、Java などの外部の言語を SQL Server に登録します。 [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) に関するページを参照してください。 |
|Java に対してサポートされるデータ型の追加|[Java のデータ型](../language-extensions/how-to/java-to-sql-data-types.md)に関するページを参照してください。|
|クエリ ストア用のカスタム キャプチャ ポリシー|有効にすると、新しいクエリ ストアのキャプチャ ポリシーの設定で、特定のサーバーでのデータ収集を微調整するための追加のクエリ ストアを使用できるようになります。 詳しくは、「[ALTER DATABASE SET オプション](../t-sql/statements/alter-database-transact-sql-set-options.md)」をご覧ください。|
|[メモリ内データベース](../relational-databases/in-memory-database.md)により、ハイブリッド バッファー プールを制御する新しい DDL 構文が追加されました。 <sup>2</sup>|[ハイブリッド バッファー プール](../database-engine/configure-windows/hybrid-buffer-pool.md)を使用すると、永続的なメモリ (PMEM) デバイス上に置かれたデータベース ファイル上のデータベース ページが必要に応じて直接アクセスされます。|
|新しいメモリ内データベース機能のメモリ最適化 tempdb メタデータが追加されました。|「[メモリ最適化 tempdb メタデータ](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata)」を参照してください。|
|リンク サーバーでは UTF-8 文字エンコードがサポートされます。 |[照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md) |
|BIN2_UTF8 照合順序名は、Latin1_General_100_BIN2_UTF8 に変更されます。 |[照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md) |
|SQL Server セットアップには、文書化されているガイドラインに従う MaxDOP の推奨事項が含まれています。 |[max degree of parallelism サーバー構成オプションの構成](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)|
|並列処理の次数とクエリ プランのメモリ許可に関する詳細が `sys.dm_exec_query_plan_stats` によって返されます。 |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| &nbsp; | &nbsp; |

><sup>1</sup> これはオプトイン機能であり、有効にするには[トレース フラグ](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 が必要です。
>
><sup>2</sup> ハイブリッド バッファー プールを有効にするためにトレース フラグは必要ではなくなりました。

### [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| 新機能または更新 | 詳細 |
|:---|:---|
|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] の Azure SQL Database マネージド インスタンス データベースのサポート。| マネージド インスタンス上で [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] をホストします。 [[!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] のインストールと構成](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb)に関するページを参照してください。
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| 新機能または更新 | 詳細 |
|:---|:---|
|計算グループを使用した表形式モデルに対する MDX クエリのサポート |このリリースで以前の[計算グループ](#calc-ctp24)での制限が削除されました。 |
|計算グループを使用したメジャーの動的な書式設定 |この機能を使用すると、[計算グループ](#calc-ctp24)を使用してメジャーの書式設定文字列を条件付きで変更できます。 たとえば、通貨換算を使用すると、さまざまな外貨形式を使ってメジャーを表示することができます。|
| &nbsp; | &nbsp; |

## <a name="ctp-25-april-2019"></a>CTP 2.5 2019 年 4 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:---|:---|
| 展開プロファイル | ビッグ データ クラスターの展開には、環境変数の代わりに、既定およびカスタマイズした[展開構成 JSON ファイル](../big-data-cluster/deployment-guidance.md#configfile)を使用します。 |
| 入力が求められる展開 | `mssqlctl cluster create` では、既定の展開に必要な設定の入力が求められるようになりました。 |
| サービス エンドポイントとのポッド名の変更 | 詳細については、[ビッグ データ クラスターのリリース ノート](../big-data-cluster/release-notes-big-data-cluster.md)をご覧ください。 |
| **mssqlctl** の機能強化 | **mssqlctl** を使用して[外部エンドポイントを一覧表示](../big-data-cluster/deployment-guidance.md#endpoints)し、**mssqlctl** のバージョンを `--version` パラメーターを使用して確認します。 |
| オフライン インストール | [ビッグ データ クラスターのオフライン展開に関するガイダンス](../big-data-cluster/deploy-offline.md)。 |
| HDFS 階層の機能強化 | Amazon S3 ストレージに対する HDFS 階層。 ADLS Gen2 の OAuth サポート。 パフォーマンス向上のためのキャッシュ機能。 詳細については、[HSDFS 階層](../big-data-cluster/hdfs-tiering.md)に関するページを参照してください。 |
| Spark to SQL Server コネクタ | [MSSQL JDBC コネクタを使用して Spark から SQL Server に読み書きする](../big-data-cluster/spark-mssql-connector.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:---|:---|
| Linux での PolyBase | 非 Hadoop コネクタ向けに Linux に [PolyBase をインストール](../relational-databases/polybase/polybase-linux-setup.md)します。<br/><br/>[PolyBase 型のマッピング](../relational-databases/polybase/polybase-type-mapping.md) |
| SQL Server 向けの新しい Java 言語 SDK | SQL Server から実行できる Java プログラムの開発を簡略化します。 「[What's new in SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)」 (SQL Server Machine Learning Services の新機能) を参照してください。 |
| DMF `sys.dm_exec_query_plan_stats` で利用可能なプランの範囲拡大 |「[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)」<sup>1</sup> を参照してください。|
| `sys.dm_exec_query_plan_stats` を有効にする新しい `LAST_QUERY_PLAN_STATS` データベース スコープの構成 |「[ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。|
| 新しい Spatial Reference Identifier (SRID) |[Australian GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) により、グローバル ポジショニング システムにより合わせたより堅牢で正確な測量基準点が提供されます。 新しい SRID は次のとおりです。<br/><br/> - 7843 - 地理 2D<br/> - 7844 - 地理 3D <br/><br/>[sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) ビューには、新しい SRID の定義が含まれています。 |
| &nbsp; | &nbsp; |

><sup>1</sup> これはオプトイン機能で、[トレース フラグ](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 を有効にするか、`LAST_QUERY_PLAN_STATS` データベース スコープの構成をオンに設定する必要があります。

## <a name="ctp-24-march-2019"></a>CTP 2.4 2019 年 3 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:---|:---|
| Spark で TensorFlow を使用しディープ ラーニングを実行する場合の GPU でのサポートに関するガイダンス。 | [GPU をサポートしているビッグ データ クラスターを展開し、TensorFlow を実行します](../big-data-cluster/spark-gpu-tensorflow.md)。 |
| データ ソース **SqlDataPool** と **SqlStoragePool** は、既定では作成されなくなりました。 | 必要に応じてこれらを手動で作成します。 [既知の問題](../big-data-cluster/release-notes-big-data-cluster.md#externaltablesctp24)を参照してください。 |
| データ プール用の `INSERT INTO SELECT` のサポート。 | 例については、「[Tutorial:Ingest data into a SQL Server data pool with Transact-SQL](../big-data-cluster/tutorial-data-pool-ingest-sql.md)」 (チュートリアル: Transact SQL を使用して SQL Server のデータ プールにデータを取り込む) を参照してください。 |
| オプション `FORCE SCALEOUTEXECUTION` と `DISABLE SCALEOUTEXECUTION` | [ビッグ データ クラスターのリリース ノート](../big-data-cluster/release-notes-big-data-cluster.md#whats-new)を参照してください。|
| 更新された AKS の展開に関する推奨事項 | AKS でビッグ データ クラスターを評価するときには、サイズ **Standard_L8s** の単一ノードを使用することをお勧めします。 |
| Spark 2.4 への Spark のランタイムのアップグレード。 | |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:-----|:-----|
|切り捨てエラー メッセージに、テーブル名および列名と切り捨てられた値が既定で含まれる。|[VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation)|
|新しい DMF `sys.dm_exec_query_plan_stats` では、ほとんどのクエリについて最後の既知の実際の実行プランと同等のものが返される。 |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
|新しい `query_post_execution_plan_profile` 拡張イベントでは、標準プロファイリングを使用する `query_post_execution_showplan` とは異なり、軽量プロファイリングに基づいて、実際の実行プランと同等のものを収集します。 |[クエリ プロファイリング インフラストラクチャ](../relational-databases/performance/query-profiling-infrastructure.md)|
|Transparent Data Encryption (TDE) のスキャン: 一時停止と再開。|[Transparent Data Encryption (TDE) のスキャン: 一時停止と再開。](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)|
| &nbsp; | &nbsp; |

><sup>1</sup> これはオプトイン機能であり、有効にするには[トレース フラグ](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 が必要です。

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)

| 新機能または更新 | 詳細 |
|:-----|:-----|
|表形式モデルでの多対多リレーションシップ。|[表形式モデルでの多対多リレーションシップ](#many-to-many-ctp24)|
|リソース ガバナンス用のプロパティ設定。|[リソース ガバナンス用のプロパティ設定](#property-ctp24)|
| &nbsp; | &nbsp; |

## <a name="ctp-23-february-2019"></a>CTP 2.3 2019 年 2 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
| :---------- | :------ |
| IntelliJ のビッグ データ クラスターでの Spark ジョブの送信。 | [IntelliJ の SQL Server ビッグ データ クラスターで Spark ジョブを送信する](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) |
| アプリケーションの展開およびクラスター管理の一般的な CLI。 | [SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリを展開する方法](../big-data-cluster/big-data-cluster-create-apps.md) |
| ビッグ データ クラスターにアプリケーションを展開するための VS Code の拡張機能。 | [VS Code を使用して SQL Server のビッグ データ クラスターにアプリケーションを展開する方法](../big-data-cluster/app-deployment-extension.md) |
| **mssqlctl**ツール コマンドの使用方法の変更。 | 詳細については、[mssqlctl の既知の問題](../big-data-cluster/release-notes-big-data-cluster.md )を参照してください。 |
| ビッグ データ クラスターで Sparklyr を使用する | [SQL Server 2019 のビッグ データ クラスターで Sparklyr を使用する](../big-data-cluster/sparklyr-from-RStudio.md) |
| **HDFS 階層**を使用した、外部の HDFS 互換ストレージのビッグ データ クラスターへのマウント。 | [HDFS 階層](../big-data-cluster/hdfs-tiering.md)に関するページを参照してください。 |
| SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイの新しい統一された接続エクスペリエンス。 | [SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイ](../big-data-cluster/connect-to-big-data-cluster.md)に関するページを参照してください。 |
| **mssqlctl cluster delete** を使用してクラスターを削除すると、ビッグ データ クラスターの一部であった名前空間内のオブジェクトのみが削除されるようになりました。 | 名前空間は削除されません。 ただし、以前のリリースでは、このコマンドを使用すると、名前空間全体が削除されました。 |
| _セキュリティ_ エンドポイントの名前が変更され、統合されました。 | **service-security-lb** と **service-security-nodeport** は、**endpoint-security** エンドポイントに統合されました。 |
| _プロキシ_ エンドポイントの名前が変更され、統合されました。 | **service-proxy-lb** と **service-proxy-nodeport** は、**endpoint-service-proxy** エンドポイントに統合されました。 |
| _コントローラー_ エンドポイントの名前が変更され、統合されました。 | **service-mssql-controller-lb** と **service-mssql-controller-nodeport** は、**endpoint-controller** エンドポイントに統合されました。 |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:-----|:-----|
|データベースごとに有効にできるデータベース復旧の高速化| [データベース復旧の高速化](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr)|
|高速順方向カーソルと静的カーソルのサポートを強制するクエリ ストア プラン|[高速順方向カーソルと静的カーソルのサポートを強制するプラン](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23) |
|複数のスコープにまたがる一時テーブルを使用するワークロードの再コンパイルの削減 |[ワークロードの再コンパイルの削減](../relational-databases/tables/tables.md#ctp23) |
|間接チェックポイントのスケーラビリティの向上 |[間接チェックポイントのスケーラビリティの向上](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23)|
|BIN2 照合順序 (`UTF8_BIN2`) で UTF-8 文字エンコードを使用するためのサポートの追加 |[照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md) |
|グラフ データベースでのエッジ制約で連鎖削除操作を定義する |[エッジ制約](../relational-databases/tables/graph-edge-constraints.md) |
|新しいデータベース スコープ構成を使用して `LIGHTWEIGHT_QUERY_PROFILING` を有効化または無効化する |[`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>ツール

| 新機能または更新 | 詳細 |
|:-----|:-----|
|Azure Data Studio での Azure Active Directory のサポート |[Azure Data Studio](../azure-data-studio/what-is.md) |
|Notebook ビュー UI が Azure Data Studio コアに移動されました。 |[Azure Data Studio でノートブックを管理する方法](../big-data-cluster/notebooks-how-to-manage.md) |
|Hadoop 分散ファイル システム (HDFS) から SQL Server ビッグ データ クラスターに外部データ ソースを作成する新しいウィザードが追加されました。 | [ツール](#tools-ctp23)|
|Notebook ビューアーの UI が強化されました。 | [ツール](#tools-ctp23) |
|新しい Notebook API が追加されました。| [ツール](#tools-ctp23) |
|Python パッケージの更新を支援するための [Reinstall Notebook dependencies]\(Notebook の依存関係の再インストール\) コマンドが追加されました。 | [ツール](#tools-ctp23) |
|SSMS から Azure Data Studio を起動します。| [ツール](#tools-ctp23) |
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| 新機能または更新 | 詳細 |
|:-----|:-----|
|テーブル モデルでの計算グループ| [テーブル モデルでの計算グループ](#calc-ctp24) |
| &nbsp; | &nbsp; |

## <a name="ctp-22-december-2018"></a>CTP 2.2 2018 年 12 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:-----|:-----|
|Azure Data Studio の SparkR のビッグ データ クラスターに対する使用 | |
|Python アプリおよび R アプリの展開|[mssqlctl を使用してアプリケーションを展開する](../big-data-cluster/big-data-cluster-create-apps.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:-----|:-----|
|SQL Server レプリケーションで UTF-8 文字エンコードを使用するためのサポートの追加 |[照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
| &nbsp; | &nbsp; |


### <a name="sql-server-on-linux"></a>Linux 上の SQL Server

| 新機能または更新 | 詳細 |
|:-----|:-----|
|Kubernetes を使用する Docker コンテナー上の Always On 可用性グループ |[コンテナー用の Always On 可用性グループ](../linux/sql-server-ag-kubernetes.md) |
| &nbsp; | &nbsp; |

## <a name="ctp-21-november-2018"></a>CTP 2.1 2018 年 11 月

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:-----|:-----|
|既定で [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の設定中に UTF-8 照合順序を選択するためのサポートが追加されました。 |[照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
|スカラー UDF のインライン化により、スカラー ユーザー定義関数 (UDF) が関係式に自動的に変換され、それらが呼び出し元の SQL クエリに埋め込まれます。 |[スカラー UDF のインライン化](../relational-databases/user-defined-functions/scalar-udf-inlining.md) |
|クエリの実行を続行する前に `SELECT` が、統計更新の同期操作の完了を待機している場合は、動的管理ビュー `sys.dm_exec_requests` の `command` 列に `SELECT (STATMAN)` が表示されます。 | [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) |
|新しい待機の種類 `WAIT_ON_SYNC_STATISTICS_REFRESH` は `sys.dm_os_wait_stats` 動的管理ビューに表示されます。 これには、統計更新の同期操作に費やされたインスタンス レベルの累積時間が表示されます。|[`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) |
|ハイブリッド バッファー プールとは、永続的なメモリ (PMEM) デバイス上に置かれたデータベース ファイル上のデータベース ページが必要に応じて直接アクセスされるという、SQL Server データベース エンジンの新しい機能です。|[ハイブリッド バッファー プール](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|グラフ一致クエリで派生テーブルまたはビューの別名を使用する |[グラフ エッジ制約](../relational-databases/tables/graph-edge-constraints.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>Linux 上の SQL Server

| 新機能または更新 | 詳細 |
|:-----|:-----|
|SQL Server 用の新しいコンテナー レジストリ |[Docker で SQL Server のコンテナーの使用を開始する](../linux/quickstart-install-connect-docker.md) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>ツール

| 新機能または更新 | 詳細 |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) は、Connect をサポートし、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ビッグ データ クラスターを管理します。 | |
| &nbsp; | &nbsp; |

## <a name="ctp-20-october-2018"></a>CTP 2.0 2018 年 10 月

### <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:-----|:-----|
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] および Spark Linux コンテナーを使用した Kubernetes へのビッグ データ クラスターのデプロイ。 | |
|HDFS からのビッグ データへのアクセス。 | |
|Spark での高度な分析と機械学習の実行。 | |
|SQL データ プールへのデータに対する Spark ストリーミングの使用。 | |
|**Azure Data Studio** でノートブック エクスペリエンスを提供するクエリ ブックを実行する。|[Data Engineering](../azure-data-studio/what-is.md#data-engineering)|
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>データベース エンジン

| 新機能または更新 | 詳細 |
|:-----|:-----|
|データベースの **COMPATIBILITY_LEVEL 150** が追加されています。 |[ALTER DATABASE 互換性レベル (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) |
|再開可能なオンライン インデックスの作成|[CREATE INDEX (Transact-SQL)](../t-sql/statements/create-index-transact-sql.md#resumable-indexes) |
|行モード メモリ許可フィードバック |[行モード メモリ許可フィードバック](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|概算 `COUNT DISTINCT`|[概数クエリ処理](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|行ストアでのバッチ モード|[行ストアでのバッチ モード](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |
|テーブル変数の遅延コンパイル|[テーブル変数の遅延コンパイル](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Java 言語拡張機能|[Java 言語拡張機能](../advanced-analytics/java/extension-java.md) |
|`MERGE` ステートメントの `MATCH` 述語を使用して、新しいデータがあるノードまたはエッジ テーブルから現在のグラフ データをマージします。 | |
|エッジ制約|[グラフ エッジ制約](../relational-databases/tables/graph-edge-constraints.md) |
|オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定| |
|可用性グループは、最大 5 つの同期セカンダリ レプリカをサポート|[可用性グループ](../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) |
|セカンダリからプライマリ レプリカへの読み取り/書き込み接続のリダイレクト|[セカンダリ レプリカからプライマリ レプリカへの読み取り/書き込み接続のリダイレクト (Always On 可用性グループ)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) |
|SQL データの検出と分類| [SQL データの検出と分類](../relational-databases/security/sql-data-discovery-and-classification.md) |
|永続メモリ デバイスの拡張サポート|[ハイブリッド バッファー プール](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|`DBCC CLONEDATABASE` での列ストア統計のサポート|[列ストア インデックスの統計 BLOB](../t-sql/database-console-commands/dbcc-clonedatabase-transact-sql.md#ctp23)|
|`sp_estimate_data_compression_savings` で導入された `COLUMNSTORE` と `COLUMNSTORE_ARCHIVE`|[列ストア インデックスに関する考慮事項](../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md#considerations-for-columnstore-indexes)|
|Windows Server フェールオーバー クラスターでの Machine Learning service のサポート |[新機能 - SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)|
|パーティション ベースのモデリングに対する Machine Learning のサポート|[新機能 - SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) |
|既定で有効になる軽量クエリ プロファイリング インフラストラクチャ |[軽量クエリ実行統計プロファイリング インフラストラクチャ v3](../relational-databases/performance/query-profiling-infrastructure.md#lightweight-query-execution-statistics-profiling-infrastructure-v3) |
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、Oracle、Teradata、MongoDB 用の新しい PolyBase コネクタ |[PolyBase とは](../relational-databases/polybase/polybase-guide.md) |
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` では、データベースでのページに関する情報が返されます。 |[sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)|
|セキュリティで保護されたエンクレーブが設定された Always Encrypted |[セキュリティで保護されたエンクレーブが設定された Always Encrypted](../relational-databases/security/encryption/always-encrypted-enclaves.md) |
|クラスター化列ストア インデックスのオンラインのビルドとリビルド |[オンラインでのインデックス操作の実行](../relational-databases/indexes/perform-index-operations-online.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>Linux 上の SQL Server

| 新機能または更新 | 詳細 |
|:-----|:-----|
|レプリケーションのサポート |[Linux での SQL Serve rのレプリケーション](../linux/sql-server-linux-replication.md)
|Microsoft 分散トランザクション コーディネーター (MSDTC) のサポート |[Linux で MSDTC を構成する方法](../linux/sql-server-linux-configure-msdtc.md) |
|サード パーティの AD プロバイダーに対する OpenLDAP のサポート |[チュートリアル: SQL Server on Linux で Active Directory 認証を使用する](../linux/sql-server-linux-active-directory-authentication.md) |
|Linux 上の Machine Learning |[Linux に Machine Learning を構成する](../linux/sql-server-linux-setup-machine-learning.md) |
| &nbsp; | &nbsp; |

### <a name="master-data-services"></a>マスター データ サービス

| 新機能または更新 | 詳細 |
|:-----|:-----|
|マスター データ サービス (MDS) ポータルが、Silverlight に依存しなくなりました。| 以前の Silverlight コンポーネントはすべて、HTML コントロールに置き換えられました。|
| &nbsp; | &nbsp; |

### <a name="security"></a>Security

| 新機能または更新 | 詳細 |
|:-----|:-----|
|SQL Server 構成マネージャーでの証明書管理|[証明書の管理 (SQL Server 構成マネージャー)](../database-engine/configure-windows/manage-certificates.md)
| &nbsp; | &nbsp; |

### <a name="tools"></a>ツール

| 新機能または更新 | 詳細 |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) は、Connect をサポートし、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ビッグ データ クラスターを管理します。 |[Azure Data Studio とは](../azure-data-studio/what-is.md)|
|SQL Server ビッグ データ クラスターを使用するシナリオのサポート |[SQL Server 2019 の拡張機能 (プレビュー)](../azure-data-studio/sql-server-2019-extension.md)|
|[**SQL Server Management Studio (SSMS) 18.0 (プレビュー)** ](../ssms/sql-server-management-studio-ssms.md): [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]をサポートします。| |
|セキュリティで保護されたエンクレーブが設定された Always Encrypted をサポートします。 |[セキュリティで保護されたエンクレーブが設定された Always Encrypted](../relational-databases/security/encryption/always-encrypted-enclaves.md)|
| &nbsp; | &nbsp; |


## <a name="other-services"></a>その他のサービス

CTP 2.4 の段階で、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]には、次のサービス用の新機能は導入されていません。

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="details"></a>詳細

### <a id="bigdatacluster"></a>ビッグ データ クラスター

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)により、次のような新しいシナリオが可能になります。

- [Spark で TensorFlow を使用しディープ ラーニングを実行する場合の GPU でのサポート](../big-data-cluster/spark-gpu-tensorflow.md)。 (CTP 2.4)
- Spark 2.4 への Spark のランタイムのアップグレード。 (CTP 2.4)
- データ プールに対する `INSERT INTO SELECT` のサポート (CTP 2.4)
- 外部テーブル クエリ用の `FORCE SCALEOUTEXECUTION` と `DISABLE SCALEOUTEXECUTION` のオプション句。 (CTP 2.4)
- [IntelliJ での [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ビッグ データ クラスターでの Spark ジョブの送信](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md)。 (CTP 2.3)
- R と Python を使用した機械学習モデルの運用、SQL Server Integration Services (SSIS) のジョブの実行など、さまざまなデータ関連アプリに関する[アプリケーションのデプロイと管理のエクスペリエンス](../big-data-cluster/big-data-cluster-create-apps.md)。 (CTP 2.3)
- [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ビッグ データ クラスター](../big-data-cluster/sparklyr-from-RStudio.md)での Sparklyr の使用。 (CTP 2.3)
- [HDFS 階層](../big-data-cluster/hdfs-tiering.md)を使用した、外部の HDFS 互換ストレージのビッグ データ クラスターへのマウント。 (CTP 2.3)
- Azure Data Studio の SparkR のビッグ データ クラスターに対する使用 (CTP 2.2)
- [Python アプリおよび R アプリを配置する](../big-data-cluster/big-data-cluster-create-apps.md)。 (CTP 2.2)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] および Spark Linux コンテナーを使用した Kubernetes へのビッグ データ クラスターのデプロイ。 (CTP 2.0)
- HDFS からのビッグ データへのアクセス。 (CTP 2.0)
- Spark での高度な分析と機械学習の実行。 (CTP 2.0)
- SQL データ プールへのデータに対する Spark ストリーミングの使用。 (CTP 2.0)
- [**Azure Data Studio**](../sql-operations-studio/what-is.md) でノートブック エクスペリエンスを提供するクエリ ブックを実行する。 (CTP 2.0)
 
[!INCLUDE [Big data clusters preview](../includes/big-data-cluster-preview-note.md)]

### <a id="databaseengine"></a>データベース エンジン

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] の次の新機能が導入または強化されています。

#### <a name="new-querypostexecutionplanprofile-extended-event-ctp-24"></a>新しい query_post_execution_plan_profile 拡張イベント (CTP 2.4)

新しい `query_post_execution_plan_profile` 拡張イベントでは、標準プロファイリングを使用する `query_post_execution_showplan` とは異なり、軽量プロファイリングに基づいて、実際の実行プランと同等のものを収集します。 詳細については、「[クエリ プロファイリング インフラストラクチャ](../relational-databases/performance/query-profiling-infrastructure.md)」を参照してください。

##### <a name="example-1---extended-event-session-using-standard-profiling"></a>例 1: 標準プロファイリングを使用した拡張イベント セッション

```sql
CREATE EVENT SESSION [QueryPlanOld] ON SERVER 
ADD EVENT sqlserver.query_post_execution_showplan(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename = N'C:\Temp\QueryPlanStd.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

##### <a name="example-2---extended-event-session-using-lightweight-profiling"></a>例 2: 軽量プロファイリングを使用した拡張イベント セッション

```sql
CREATE EVENT SESSION [QueryPlanLWP] ON SERVER 
ADD EVENT sqlserver.query_post_execution_plan_profile(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename=N'C:\Temp\QueryPlanLWP.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

#### <a name="new-dmf-sysdmexecqueryplanstats-ctp-24"></a>新しい DMF sys.dm_exec_query_plan_stats (CTP 2.4) 

新しい DMF `sys.dm_exec_query_plan_stats` では、軽量プロファイリングに基づいて、ほとんどのクエリについて最後の既知の実際の実行プランと同等のものが返されます。 詳細については、[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) に関するページと「[クエリ プロファイリング インフラストラクチャ](../relational-databases/performance/query-profiling-infrastructure.md)」を参照してください。 例として、次のスクリプトをご覧ください。

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

これはオプトイン機能であり、有効にするには[トレース フラグ](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 が必要です。

#### <a name="transparent-data-encryption-tde-scan---suspend-and-resume-ctp-24"></a>Transparent Data Encryption (TDE) スキャン: 一時停止および再開 (CTP 2.4)

データベースで [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md) を有効にするには、各ページをデータ ファイルからバッファー プールに読み込み、暗号化されたページをディスクから書き戻す暗号化のスキャンを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で実行する必要があります。 ユーザーが暗号化のスキャンをより制御できるよう、構文の一時停止および再開が可能な、TDE スキャンが [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] に導入されています。これでは、システムでワークロードが多い場合やビジネスに極めて重要な時間のときはスキャンを一時停止し、後でスキャンを再開できます。

TDE 暗号化のスキャンを一時停止するには、次の構文を使用します。

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

同様に、次の構文で TDE 暗号化のスキャンを再開できます。

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

暗号化のスキャンの現在の状態を示すために、`sys.dm_database_encryption_keys` 動的管理ビューに `encryption_scan_state` が追加されています。 また、暗号化のスキャンの状態が最後に変更された日時を含む `encryption_scan_modify_date` という新しい列もあります。 暗号化のスキャンが一時停止中に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが再開された場合、一時停止されているスキャンがあることが起動時にエラー ログに記述されます。

#### <a name="accelerated-database-recovery-ctp-23"></a>高速データベース復旧 (CTP 2.3)

[高速データベース復旧](/azure/sql-database/sql-database-accelerated-database-recovery/)では、SQL Server データベース エンジンの復旧プロセスの再設計により、データベースの可用性が大幅に向上します (実行時間の長いトランザクションが存在する場合は特に)。 [データベース復旧](../relational-databases/logs/the-transaction-log-sql-server.md?#recovery-of-all-incomplete-transactions-when--is-started)とは、トランザクション的に一貫した (クリーンな) 状態で各データベースを開始させるために SQL Server で使用されるプロセスです。 高速データベース復旧が有効なデータベースでは、フェールオーバーまたは他のクリーンではないシャットダウンの後の復旧が、非常に速く完了します。 CTP 2.3 以降では、次の構文を使用してデータベースごとに高速データベース復旧を有効にできます。

```sql
ALTER DATABASE <db_name> SET ACCELERATED_DATABASE_RECOVERY = {ON | OFF}
```

> [!NOTE]
> 上記の構文を使用しなくても、Azure SQL DB でこの機能を使用できます。この機能は、[パブリック プレビュー中、要求に応じて有効にされます](/azure/sql-database/sql-database-accelerated-database-recovery)。 この機能は、有効にされた後は、既定でオンになります。

大規模なトランザクションの多いクリティカルなデータベースがある場合は、プレビュー期間中にこの機能を試してください。 フィードバックを[[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]チーム](<https://aka.ms/sqlfeedback>)にお送りください。

#### <a name="query-store-plan-forcing-support-for-fast-forward-and-static-cursors-ctp-23"></a>高速順方向カーソルと静的カーソルのサポートを強制するクエリ ストア プラン (CTP 2.3)

クエリ ストアでは、高速順方向カーソルおよび T-SQL と API の静的カーソルに対してクエリ実行プランを強制する機能がサポートされるようになりました。 強制は、`sp_query_store_force_plan` または SQL Server Management Studio のクエリ ストア レポートによってサポートされます。

#### <a name="reduced-recompilations-for-workloads-using-temporary-tables-across-multiple-scopes-ctp-23"></a>複数のスコープにまたがる一時テーブルを使用するワークロードの再コンパイルの削減 (CTP 2.3)

この機能が提供されるまでは、一時テーブルが外側のスコープのバッチによって作成されていた場合、データ操作言語 (DML) ステートメント (`SELECT`、`INSERT`、`UPDATE`、`DELETE`) で一時テーブルを参照すると、実行のたびに DML ステートメントが再コンパイルされました。 この改良により、SQL Server では追加の軽量なチェックが実行されて、不要な再コンパイルが回避されます。

- コンパイル時に一時テーブルの作成に使用される外側のスコープのモジュールが、連続実行に使用されるものと同じかどうかを確認してください。 
- 最初のコンパイルで行われたデータ定義言語 (DDL) のすべての変更を追跡し、連続実行に対する DDL 操作と比較します。 

最終的な結果は、余分な再コンパイルと CPU のオーバーヘッドを削減することです。

#### <a name="improved-indirect-checkpoint-scalability-ctp-23"></a>間接チェックポイントのスケーラビリティの向上 (CTP 2.3)

以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、tempdb のように多数のダーティ ページを生成するデータベースがあると、応答停止スケジューラ エラーが発生することがあります。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]では間接チェックポイントのスケーラビリティが向上しており、UPDATE/INSERT のワークロードが大きいデータベースでのエラー回避に役立つはずです。

#### <a name="utf-8-support-ctp-23"></a>UTF-8 のサポート (CTP 2.3)

インポートまたはエクスポートのエンコードとして、あるいはテキスト データのデータベース レベルまたは列レベルの照合順序としての、広く使用されている UTF-8 文字エンコードの完全なサポート。 UTF-8 は、`CHAR` および `VARCHAR` データ型で許可されており、`UTF8` サフィックスを持つようにオブジェクトの照合順序を作成するか変更すると有効になります。 

たとえば、`LATIN1_GENERAL_100_CI_AS_SC` を `LATIN1_GENERAL_100_CI_AS_SC_UTF8` に変更するような場合です。 UTF-8 は、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] で導入された補助文字をサポートする Windows 照合順序にのみ使用できます。 `NCHAR` および `NVARCHAR` では UTF-16 エンコードのみが許可され、変更されていません。

使用されている文字セットによっては、この機能によりストレージを大幅に節約できます。 たとえば、ASCII (ラテン) 文字列の既存の列データ型を、UTF-8 対応の照合順序を使用して `NCHAR(10)` から `CHAR(10)` に変更すると、必要なストレージが 50% 削減されます。 このように減るのは、`NCHAR(10)` を保存するには 20 バイト必要であるのに対し、`CHAR(10)` では同じ Unicode 文字列に 10 バイトしか必要ないためです。

詳細については、「 [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。

**CTP 2.1** 既定で [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の設定中に UTF-8 照合順序を選択するためのサポートが追加されました。

**CTP 2.2** SQL Server レプリケーションで UTF-8 文字エンコードを使用するためのサポートが追加されました。

**CTP 2.3** BIN2 照合順序 (UTF8_BIN2) で UTF-8 文字エンコードを使用するためのサポートが追加されました。

#### <a name="scalar-udf-inlining-ctp-21"></a>スカラー UDF のインライン化 (CTP 2.1)

スカラー UDF のインライン化では、スカラー ユーザー定義関数 (UDF) が関係式に変換され、それらが呼び出し元の SQL クエリに埋め込まれます。これにより、スカラー UDF を利用するワークロードのパフォーマンスが向上します。 スカラー UDF のインライン化によって、UDF 内の操作に対するコストに基づく最適化が促進され、その結果として、非効率な、反復的および直列的な実行プランではなく、セット指向で並列的である効率的なプランが提供されます。 この機能は、データベース互換性レベル 150 では既定で有効です。

詳細については、「[スカラー UDF のインライン化](../relational-databases/user-defined-functions/scalar-udf-inlining.md)」を参照してください。

#### <a name="a-nametruncation-truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a><a name="truncation" />テーブル名および列名と切り捨てられた値を取り込むように改善された切り捨てエラー メッセージ (CTP 2.1)

エラー メッセージ ID 8152 `String or binary data would be truncated` は、データ移動ワークロードの開発または管理を行う多くの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 開発者や管理者によく知られています。このエラーは、スキーマが異なるソースと変換先との間でのデータ転送中に、ソース側のデータが大きすぎて変換先のデータ型に収まり切らない場合に発生します。 このエラー メッセージはトラブルシューティングに時間がかかることがあります。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、次のシナリオに対してより具体的な新しいエラー メッセージ (2628) が導入されています。  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

新しいエラー メッセージである 2628 では切り捨て問題に関してより多くのコンテキストが表示されます。このため、トラブルシューティング プロセスが簡単になります。 

**CTP 2.1 と CTP 2.2** これはオプトイン エラー メッセージであり、使用するには[トレース フラグ](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460 を有効にする必要があります。

**CTP 2.4** エラー メッセージ 2628 が既定の切り捨てのメッセージとなり、データベース互換性レベル 150 下でエラー メッセージ 8152 が置き換えられます。 データベースの互換性レベルが 150 の場合、エラー メッセージ 2628 と 8152 を切り替えるために、新しいデータベース スコープ構成の `VERBOSE_TRUNCATION_WARNINGS` が導入されました。 詳細については、「[ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。
データベース互換性レベルが 140 以下の場合、エラー メッセージ 2628 が、[トレース フラグ](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460 を有効にする必要があるオプトインのエラー メッセージとなります。

#### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>統計情報のブロックに関する診断データが改善されている (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、統計更新の同期操作を待機する、実行時間の長いクエリに対する診断データが改善されています。 クエリの実行を続行する前に `SELECT` が、統計更新の同期操作の完了を待機している場合は、動的管理ビュー `sys.dm_exec_requests` の `command` 列に `SELECT (STATMAN)` が表示されます。 さらに、新しい待機の種類 `WAIT_ON_SYNC_STATISTICS_REFRESH` は `sys.dm_os_wait_stats` 動的管理ビューに表示されます。 これには、統計更新の同期操作に費やされたインスタンス レベルの累積時間が表示されます。

#### <a name="hybrid-buffer-pool-ctp-21"></a>ハイブリッド バッファー プール (CTP 2.1)

ハイブリッド バッファー プールとは、永続的なメモリ (PMEM) デバイス上に置かれたデータベース ファイル上のデータベース ページが必要に応じて直接アクセスされるという、SQL Server データベース エンジンの新しい機能です。 PMEM デバイスを使用すると、データ アクセスにおける待機時間が非常に短くなるので、エンジンはバッファー プール内の "クリーンなページ" 領域にデータのコピーを作成するのをやめて、単純に PMEM 上のページに直接アクセスすることができます。 エンライトメントの場合と同様に、アクセスはメモリ マップ I/O を使用して実行されます。 この場合は、DRAM にページをコピーすることが回避され、さらに永続的ストレージ上のページにアクセスするときにオペレーティング システムの I/O スタックが回避されることから、パフォーマンス上の利点がもたらされます。 この機能は SQL Server on Windows と SQL Server on Linux の両方で利用できます。

詳細については、「[Hybrid buffer pool](../database-engine/configure-windows/hybrid-buffer-pool.md)」 (ハイブリッド バッファー プール) を参照してください

#### <a name="static-data-masking-ctp-21"></a>静的データ マスク (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では静的データ マスクが導入されています。 静的データ マスクを使用することで、SQL Server データベースのコピー内の機密データをサニタイズすることができます。 静的データ マスクは、データベースのサニタイズされたコピーを作成するのに役立ちます。このコピーでは、非運用環境のユーザーと共有可能なコピーが作成されるようにすべての機密情報が変更されています。 静的データ マスクは、開発、テスト、分析、ビジネス レポート、コンプライアンス、トラブルシューティングのほか、特定のデータを異なる環境にコピーしてはならないシナリオで使用することができます。

静的データ マスクは、列レベルで動作します。 マスクする列を選択し、選択した列ごとにマスク関数を指定します。 静的データ マスクでは、データベースがコピーされてから、指定したマスク関数が列に適用されます。

##### <a name="static-data-masking-vs-dynamic-data-masking"></a>静的データ マスクと動的データ マスクの比較

データ マスクとは、データベースに対してマスクを適用することで機密情報を非表示にすると共に、機密情報を新しいデータまたはスクラブ データに置換するプロセスです。 Microsoft では 2 つのマスク オプションを提供しています。静的データ マスクと動的データ マスクです。 動的データ マスクは、[!INCLUDE[ssSQL16](../includes/sssql16-md.md)] で導入されています。 次の表で、この 2 つのソリューションを比較します。

|静的データ マスク |動的なデータ マスキング|
|:----|:----|
|データベースのコピーに対して行われます <br/><br/>元のデータを取得できません<br/><br/>マスクはストレージ レベルに実行されます<br/><br/>すべてのユーザーが同じマスクされたデータにアクセスできます<br/><br/>継続的なチーム全体のアクセスを目的としています|元のデータベースに対して行われます<br/><br/>元のデータはそのまま保持されます<br/><br/>マスクはクエリ時にその場で実行されます<br/><br/>マスクはユーザーのアクセス許可に基づいて変化します <br/><br/>時間どおりのユーザー固有のアクセスを目的としています|

#### <a name="database-compatibility-level-ctp-20"></a>データベース互換レベル (CTP 2.0)

データベースの **COMPATIBILITY_LEVEL 150** が追加されています。 特定のユーザー データベースに対して有効にするには、次のコマンドを実行します。

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

#### <a name="resumable-online-index-create-ctp-20"></a>再開可能なオンライン インデックスの作成 (CTP 2.0)

**再開可能なオンライン インデックスの作成**により、インデックス作成操作が一時停止しても、最初からやり直すのではなく、操作が一時停止または失敗した場所から後で再開できます。

再開可能なオンライン インデックス作成では次のシナリオがサポートされています。
- インデックスの作成が失敗した後で、インデックス作成操作を再開します (データベースのフェールオーバー後や、ディスク領域が不足した後など)。
- 実行中のインデックス作成操作を一時停止し、後で再開することで、必要なシステム リソースを一時的に解放できます。
- 多くのログ領域と、他のメンテナンス アクティビティをブロックしてログが切り捨てられる実行時間の長いトランザクションを使用することなく、大きなインデックスを作成します。

この機能がないと、インデックス作成が失敗した場合、オンライン インデックス作成操作を最初からもう一度実行する必要があります。

このリリースでは、この機能を追加する再開可能機能を[再開可能なオンライン インデックス再構築](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/)に拡張します。

さらに、[オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)を使用して、特定のデータベースに対する既定値としてこの機能を設定できます。

詳しくは、[再開可能なオンライン インデックス作成](../t-sql/statements/create-index-transact-sql.md#resumable-indexes)に関する記事をご覧ください。

#### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>クラスター化列ストア インデックスのオンラインのビルドとリビルド (CTP 2.0)

行ストア テーブルを列ストア形式に変換します。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、クラスター化列ストア インデックス (CCI) の作成はオフラインのプロセスで、CCI の作成中はすべての変更を停止する必要がありました。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] および [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] では、CCI をオンラインで作成または再作成できます。 ワークロードはブロックされず、基になるデータに対するすべての変更はターゲットの列ストア テーブルに透過的に追加されます。 使用できる新しい [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの例を次に示します。

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

#### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted (CTP 2.0)

インプレースの暗号化と高度な計算で Always Encrypted を拡張します。 拡張は、サーバー側のセキュリティ エンクレーブ内でプレーンテキスト データに対する計算を有効にすることによって行われます。

暗号化操作には、列の暗号化と、列暗号化キーのローテーションが含まれます。 これらの操作は [!INCLUDE[tsql](../includes/tsql-md.md)] を使用して発行でき、データベースから外にデータを移動する必要ありません。 セキュア エンクレーブでは、次の要件が両方ともある広範なシナリオのセットに Always Encrypted が提供されます。  

- データベース管理者、システム管理者、クラウド オペレーター、マルウェアなど、高い特権を持ちながら承認されていないユーザーから機密データが保護する必要がある。
- 保護されたデータに対する高度な計算がデータベース システム内でサポートされている必要がある。

詳しくは、「[Always Encrypted with secure enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md)」(セキュア エンクレーブを使用する Always Encrypted) をご覧ください。

> [!NOTE]
> セキュア エンクレーブを使用する Always Encrypted は、Windows OS でのみ使用できます。

#### <a name="intelligent-query-processing-ctp-20"></a>インテリジェントなクエリ処理 (CTP 2.0)

- **行モード メモリ許可フィードバック**は、バッチ モードと行モード両方の演算子のメモリ許可サイズを調整することにより、[!INCLUDE[ssSQL17](../includes/sssql17-md.md)] で導入されたメモリ許可フィードバックの機能を拡張します。 メモリ許可条件が過剰な場合、許可されるメモリが実際に使われるメモリ サイズの 2 倍より多いと、メモリ許可フィードバックはメモリ許可を再計算します。 その後は、連続実行で要求されるメモリが少なくなります。 メモリ許可が過少な場合、ディスクへの書き込みが発生すると、メモリ許可フィードバックはメモリ許可の再計算をトリガーします。 その後は、連続実行で要求されるメモリが多くなります。 この機能は、データベース互換性レベル 150 では既定で有効です。

- **概算 COUNT DISTINCT** は、グループ内の一意の非 null 値の概数を返します。 この関数は、ビッグ データのシナリオで使用するために設計されています。 この関数は、次の条件がすべて満たされるクエリ向けに最適化されています。
   - 数百万行以上のデータ セットにアクセスする。
   - 多数の個別値を持つ 1 つまたは複数の列を集計する。
   - 絶対的な精度より応答性が重視される。
      - 通常、`APPROX_COUNT_DISTINCT` は正確な答の 2% 以内の結果を返します。
      - 正確な答に必要な時間より短い時間で、おおよその答を返します。

- **行ストアのバッチ モード**では、バッチ モードでクエリを処理するのに列ストア インデックスが不要になりました。 バッチ モードのクエリ演算子は、一度に 1 行だけでなく、行のセットを処理できます。 この機能は、データベース互換性レベル 150 では既定で有効です。 次のすべてが当てはまる場合、行ストア テーブルにアクセスするクエリはバッチ モードによって速度が向上します。
   - クエリで、結合や集計演算子などの分析演算子が使用されている。
   - クエリに 100,000 行以上が関係する。
   - クエリが、入力/出力データ バインドではなく CPU バインドである。
   - 列ストア インデックスを作成して使用すると、次のいずれかの欠点がある。
      - クエリに加わるオーバーヘッドが大きすぎる。
      - 列ストア インデックスでまだサポートされていない機能に依存するアプリケーションのため不可能である。

- **テーブル変数の遅延コンパイル**を使用すると、テーブル変数を参照するクエリのプランの品質および全体的なパフォーマンスが向上します。 最適化と最初のコンパイルの実行中に、この機能は実際テーブル変数の行数に基づくカーディナリティの推定を反映します。 この正確な行数の情報は、ダウンストリーム プラン操作を最適化するために使用されます。 この機能は、データベース互換性レベル 150 では既定で有効です。

インテリジェントなクエリ処理機能を使用するには、データベースを `COMPATIBILITY_LEVEL = 150` に設定します。

#### <a id="programmability"></a> Java 言語のプログラミング機能の拡張 (CTP 2.0)

- **Java 言語拡張機能 (プレビュー)** :Java 言語の拡張機能を使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で Java コードを実行します。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、機能 "Machine Learning Services (データベース内)" を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに追加すると、この拡張機能がインストールされます。

#### <a id="sqlgraph"></a> SQL グラフ機能 (CTP 2.3)

- **グラフ一致クエリで派生テーブルまたはビューの別名を使用する (CTP 2.1)** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]上でのグラフ クエリでは、`MATCH` 構文内にビューおよび派生テーブルの別名を使用することがサポートされています。 `MATCH` 内でこれらの別名を使用するには、`UNION ALL` 演算子を使用して、ノード テーブルのセットまたはエッジ テーブルのセットのいずれかに対してビューおよび派生テーブルを作成する必要があります。 ノードまたはエッジのテーブルでは、フィルターが用意されている場合もあればそうでない場合もあります。 `MATCH` クエリ内で派生テーブルおよびビューの別名を使用する機能は、ご利用のグラフ内の 2 つ以上のエンティティ間で、異種のエンティティまたは異種の接続についてクエリを実行したいというシナリオにおいて非常に便利です。

- **`MERGE` DML での一致サポート (CTP 2.0)** を使用すると、個別の `INSERT`、`UPDATE`、または `DELETE` ステートメントではなく、単一のステートメントでグラフのリレーションシップを指定できます。 `MERGE` ステートメントの `MATCH` 述語を使用して、新しいデータがあるノードまたはエッジ テーブルから現在のグラフ データをマージします。 この機能により、エッジ テーブルでの `UPSERT` シナリオが可能になります。 ユーザーは 1 つのマージ ステートメントを使用して、2 つのノードの間で、新しいエッジを挿入したり、既存のエッジを更新したりできます。

- **エッジ制約 (CTP 2.0)** が SQL グラフのエッジ テーブルに導入されています。 エッジ テーブルは、任意のノードをデータベース内の他の任意のノードに接続できます。 エッジ制約の導入により、この動作にいくつかの制限を適用できるようになります。 新しい `CONNECTION` 制約を使用して、特定のエッジ テーブルが接続できるノードの種類をスキーマで指定できます。 

  **(CTP 2.3)** この機能をさらに拡張すると、エッジ制約で連鎖削除操作を定義できます。 特定のエッジが接続しているノードをユーザーが削除したときのデータベース エンジンの動作を定義できます。

#### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations-ctp-20"></a>オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定 (CTP 2.0)

- **オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定**では、データベース レベルで `ONLINE` と `RESUMABLE` のインデックス操作に対して既定の動作を設定できます。インデックスの作成や再構築などの個々のインデックス DDL ステートメントごとにこれらのオプションを定義する必要はありません。

- これらの既定値は、データベース スコープの構成オプション `ELEVATE_ONLINE` と `ELEVATE_RESUMABLE` を使用して設定します。 いずれのオプションでも、エンジンはサポートされる操作をオンラインまたは再開可能のインデックス実行に自動昇格します。 これらのオプションを使用して、次の動作を有効にできます。

  - `FAIL_UNSUPPORTED` オプションでは、すべてのインデックス操作がオンラインまたは再開可能を許可され、オンラインまたは再開可能をサポートされていないインデックス操作は失敗します。
  - `WHEN_SUPPPORTED` オプションでは、サポートされている操作はオンラインまたは再開可能を許可され、サポートされていない操作はオフラインまたは再開不可能で実行されます。
  - `OFF` オプションでは、DDL ステートメントで明示的に指定されていない限り、すべてのインデックス操作をオフラインと再開不可能で実行する現在の動作が許可されます。

既定の設定をオーバーライドするには、`ONLINE` または `RESUMABLE` オプションをインデックスの作成および再構築コマンドで指定します。 

この機能がないと、インデックスの作成や再構築などのインデックス DDL ステートメントで、オンラインおよび再開可能のオプションを直接指定する必要があります。

再開可能なインデックスの詳細については、[再開可能なオンライン インデックスの作成](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/)に関するページを参照してください。

#### <a id="ha"></a>Always On 可用性グループ - 同期レプリカの増加 (CTP 2.0)

- **最大 5 つの同期レプリカ**: [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] では 3 つであった同期レプリカの最大数が、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]では 5 つに増加します。 この 5 つのレプリカのグループを、グループ内で自動フェールオーバーするように構成できます。 1 つのプライマリ レプリカと、4 つの同期セカンダリ レプリカがあります。

- **セカンダリ レプリカからプライマリ レプリカへの接続のリダイレクト**:接続文字列に指定されたターゲット サーバーに関係なく、クライアント アプリケーションの接続先をプライマリ レプリカにすることができます。 この機能により、リスナーなしで接続をリダイレクトできます。 次のような場合に、セカンダリ レプリカからプライマリ レプリカへの接続のリダイレクトを使用します。

  - クラスター テクノロジでリスナー機能が提供されていない。
  - リダイレクトが複雑になるマルチ サブネット構成。
  - クラスターの種類が `NONE` である読み取りスケールアウトまたはディザスター リカバリーのシナリオ。

詳しくは、「[セカンダリからプライマリ レプリカへの読み取り/書き込み接続のリダイレクト (Always On 可用性グループ)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md)」をご覧ください。

#### <a name="data-discovery-and-classification-ctp-20"></a>データの検出と分類 (CTP 2.0)

データの検出と分類では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にネイティブに組み込まれた高度な機能が提供されます。 最も機密性の高いデータの分類とラベル付けには、次のような利点があります。
- データのプライバシーに関する基準と規制のコンプライアンス要件を満たすのに役立ちます。
- 監視 (監査) や、機密データへの異常アクセスに対するアラートなど、セキュリティ シナリオをサポートします。
- 企業内で機密データが存在する場所を識別しやすくなるので、管理者はデータベースをセキュリティで保護する適切な手順を実行できます。

詳しくは、「[SQL データの検出と分類](../relational-databases/security/sql-data-discovery-and-classification.md)」をご覧ください。

[監査](../relational-databases/security/auditing/sql-server-audit-database-engine.md)も、新しいフィールド `data_sensitivity_information` が監査ログに追加されて強化されました。このフィールドには、クエリによって返された実際のデータの機密度の分類 (ラベル) が記録されます。 詳細と例については、「[ADD SENSITIVITY CLASSIFICATION](../t-sql/statements/add-sensitivity-classification-transact-sql.md)」をご覧ください。

>[!NOTE]
>監査を有効にする方法についての変更はありません。 監査レコードには、新しいフィールド `data_sensitivity_information` が追加されています。このフィールドには、クエリによって返された実際のデータの機密度の分類 (ラベル) が記録されます。 「[機密データへのアクセスの監査](/azure/sql-database/sql-database-data-discovery-and-classification/#subheading-3)」をご覧ください。

#### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>永続メモリ デバイスの拡張サポート (CTP 2.0)

永続メモリ デバイスに配置されるすべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ファイルが、"*エンライト化*" モードで動作できるようになりました。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、効率的な memcpy 操作を使用してオペレーティング システムのストレージ スタックをバイパスし、デバイスに直接アクセスします。 このモードでは、このようなデバイスに対して低遅延の入力/出力が許可されるので、パフォーマンスが向上します。
    - たとえば、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には次のようなファイルが含まれます。
        - データベース ファイル
        - トランザクション ログ ファイル
        - インメモリ OLTP チェックポイント ファイル
    - 永続メモリは、ストレージ クラス メモリとも呼ばれます。
    - 永続メモリは、Microsoft 以外の Web サイトでは非公式に *pmem* と呼ばれることがあります。

> [!NOTE]
> このプレビュー リリースでは、永続メモリ デバイス上のファイルのエンライトメントは Linux でのみ利用できます。 Windows 上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] 以降で永続メモリ デバイスがサポートされています。

#### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>DBCC CLONEDATABASE での列ストア統計のサポート (CTP 2.0)

`DBCC CLONEDATABASE` では、データをコピーすることなく、クエリのパフォーマンスに関する問題のトラブルシューティングに必要なすべての要素を含むスキーマのみのデータベースのコピーが作成されます。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のコマンドでは、列ストア インデックスのクエリのトラブルシューティングを正確に行うために必要な統計情報がコピーされず、手作業でこの情報をキャプチャする必要がありました。 現在の [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の `DBCC CLONEDATABASE` では、列ストア インデックスの統計 BLOB が自動的にキャプチャされるので、手動で行う必要ありません。

#### <a name="new-options-added-to-spestimatedatacompressionsavings-ctp-20"></a>sp_estimate_data_compression_savings に追加された新しいオプション (CTP 2.0)

`sp_estimate_data_compression_savings` は、要求されたオブジェクトの現在のサイズ、および要求された圧縮状態での推定オブジェクト サイズを返します。 現在、このプロシージャでは、`NONE`、`ROW`、`PAGE` の 3 つのオプションがサポートされています。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、`COLUMNSTORE` と `COLUMNSTORE_ARCHIVE` の 2 つの新しいオプションが導入されています。 これらの新しいオプションを使用すると、標準またはアーカイブいずれかの列ストア圧縮を使用してテーブルに列ストア インデックスを作成した場合に節約される領域を見積もることができます。

#### <a id="ml"></a> SQL Server Machine Learning Services フェールオーバー クラスターとパーティション ベースのモデリング (CTP 2.0)

- **パーティション ベースのモデリング**:`sp_execute_external_script` に追加された新しいパラメーターを使用し、データのパーティションごとに外部スクリプトが処理されます。 この機能は、1 つの大きいモデルではなく、多数の小さいモデル (データのパーティションごとに 1 つのモデル) のトレーニングをサポートします。

- **Windows Server フェールオーバー クラスター**:Windows Server フェールオーバー クラスター上の Machine Learning Services に高可用性を構成します。

詳しくは、「[What's new in SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)」(SQL Server Machine Learning Services の新機能) をご覧ください。

#### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>既定で有効になる軽量クエリ プロファイリング インフラストラクチャ (CTP 2.0)

軽量クエリ プロファイリング インフラストラクチャ (LWP) では、標準のプロファイリング メカニズムよりも効率的にクエリのパフォーマンス データが提供されます。 軽量プロファイリングが既定で有効になるようになりました。 この機能は、[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 で導入されました。 軽量プロファイリングでは推定 2% の CPU オーバーヘッドでクエリ実行統計コレクション メカニズムが提供されるのに対し、標準クエリ プロファイリング メカニズムでは最大 75% の CPU オーバーヘッドが発生します。 以前のバージョンでは、既定ではオフでした。 データベース管理者は、[トレース フラグ 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) でこの機能を有効にできます。 

軽量プロファイリングの詳細については、[クエリ プロファイリング インフラストラクチャ](../relational-databases/performance/query-profiling-infrastructure.md)に関するページを参照してください。

**CTP 2.3** 新しいデータベース スコープの構成 `LIGHTWEIGHT_QUERY_PROFILING` が、軽量クエリ プロファイリング インフラストラクチャを有効または無効にするために導入されました。

#### <a id="polybase"></a>新しい PolyBase コネクタ

- **[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、Oracle、Teradata、MongoDB 用の新しいコネクタ**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、Oracle、Teradata、および MongoDB 用に外部データへの新しいコネクタが導入されています。

#### <a name="new-sysdmdbpageinfo-system-function-returns-page-information-ctp-20"></a>ページ情報を返す新しい sys.dm_db_page_info システム関数 (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` では、データベースでのページに関する情報が返されます。 この関数では、`object_id`、`index_id`、`partition_id` など、ページからのヘッダー情報を含む行が返されます。 この関数を使用すると、ほとんどの場合に `DBCC PAGE` を使用する必要がなくなります。 

ページ関連の待機のトラブルシューティングを容易にするため、page_resource という名前の新しい列も `sys.dm_exec_requests` と `sys.sysprocesses` に追加されました。 この新しい列を使用すると、別の新しいシステム関数 `sys.fn_PageResCracker` を介して、これらのビューに `sys.dm_db_page_info` を結合できます。 例として、次のスクリプトをご覧ください。

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

### <a id="sqllinux"></a> SQL Server on Linux

- **Kubernetes に対する Docker コンテナー上の Always On 可用性グループ (CTP 2.2)** :Kubernetes は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで実行されているコンテナーを調整して、SQL Server Always On 可用性グループで高可用性のデータベース セットを提供できます。 Kubernetes オペレーターは、**mssql-server コンテナー**と正常性モニターを備えたコンテナーを含む StatefulSet をデプロイします。

- **新しいコンテナー レジストリ (CTP 2.1)** :[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] および [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] のすべてのコンテナー イメージが、Microsoft Container Registry に格納されるようになります。 Microsoft Container Registry は、Microsoft 製品のコンテナーを配布するための公式のコンテナー レジストリです。 さらに、認定された RHEL ベースのイメージが発行されるようになります。

  - Microsoft Container Registry: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - 認定済みの RHEL ベースのコンテナー イメージ: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

- **レプリケーションのサポート (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、Linux での SQL Server レプリケーションがサポートされています。 SQL エージェントを備えた Linux 仮想マシンは、パブリッシャー、ディストリビューター、またはサブスクライバーになることができます。 

  次の種類のパブリケーションを作成します。
  - トランザクション
  - スナップショット
  - Merge

  レプリケーション [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を構成するか、または[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)を使用します。

- **Microsoft 分散トランザクション コーディネーター (MSDTC) のサポート (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] on Linux では、Microsoft 分散トランザクション コーディネーター (MSDTC) がサポートされています。 詳しくは、「[How to configure MSDTC on Linux](../linux/sql-server-linux-configure-msdtc.md)」(Linux で MSDTC を構成する方法) をご覧ください。

- **サード パーティの AD プロバイダーに対する OpenLDAP のサポート (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] on Linux は OpenLDAP をサポートしているので、サード パーティのプロバイダーが Active Directory に参加できます。

- **Linux での Machine Learning (CTP 2.0)** :[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services (データベース内) が Linux でサポートされるようになりました。 サポートには、`sp_execute_external_script` ストアド プロシージャが含まれます。 Linux に Machine Learning Services をインストールする方法については、R と Python をサポートする Machine Learning Services の Linux への[インストール[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]に関するページ](../linux/sql-server-linux-setup-machine-learning.md)をご覧ください。

### <a id="mds"></a> Master Data Services 

- **Silverlight コントロールの HTML への置き換え (CTP 2.0)** : マスター データ サービス (MDS) ポータルが、Silverlight に依存しなくなりました。 以前の Silverlight コンポーネントはすべて、HTML コントロールに置き換えられました。

### <a id="security"></a>セキュリティ

- **SQL Server 構成マネージャーでの証明書管理 (CTP 2.0)** : SSL/TLS 証明書は、SQL Server インスタンスへのアクセスをセキュリティで保護するために広く使われています。 証明書の管理が SQL Server 構成マネージャーに統合され、次のような一般的なタスクが簡単になりました。

  - [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスにインストールされている証明書の表示と検証。 
  - 有効期限が近い証明書の表示。
  - Always On 可用性グループに参加しているコンピューターへの証明書の展開 (プライマリ レプリカを保持するノードから)。
  - フェールオーバー クラスター インスタンスに参加しているコンピューターへの証明書の展開 (アクティブなノードから)。

  > [!NOTE]
  > ユーザーには、すべてのクラスター ノードでの管理者権限が必要です。

### <a id="tools"></a>ツール

- [**Azure Data Studio**](../azure-data-studio/what-is.md):以前 SQL Operations Studio というプレビュー名でリリースされていた Azure Data Studio は、軽量、最新、オープン ソース、クロスプラットフォームのデスクトップ ツールであり、データの開発と管理におけるほとんどの一般的なタスクに対応します。 Azure Data Studio と [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] プレビュー拡張機能](../azure-data-studio/sql-server-2019-extension.md)を使用すると、オンプレミスおよびクラウドの Windows、macOS、Linux 上の SQL Server に接続できます。 Azure Data Studio では次のことができます。

<a name = "tools-ctp23"></a>

  - AAD がサポートされるようになりました。 (CTP 2.3)
  - Notebook ビュー UI が Azure Data Studio コアに移動されました。 (CTP 2.3)
  - Hadoop 分散ファイル システム (HDFS) から SQL Server ビッグ データ クラスターに外部データ ソースを作成する新しいウィザードが追加されました。 (CTP 2.3)
  - Notebook ビューアーの UI が強化されました。 (CTP 2.3)
  - 新しい Notebook API が追加されました。 (CTP 2.3)
  - Python パッケージの更新を支援するための [Reinstall Notebook dependencies]\(Notebook の依存関係の再インストール\) コマンドが追加されました。 (CTP 2.3)
  - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ビッグ データ クラスターに接続して管理します。 (CTP 2.1)
  - 非常に高速の Intellisense、コード スニペット、ソース管理が統合された最新の開発環境で、クエリを編集して実行できます。 (CTP 2.0) 
  - 組み込まれている結果セット グラフ化機能を使用して、すばやくデータを視覚化できます。 (CTP 2.0)
  - カスタマイズ可能なウィジェットを使用して、サーバーおよびデータベース用のカスタム ダッシュボードを作成できます。 (CTP 2.0)  
  - 組み込みのターミナルを使用して、広範な環境を簡単に管理できます。 (CTP 2.0)
  - Jupyter を基に構築された統合ノートブック エクスペリエンスでデータを分析できます。 (CTP 2.0)
  - カスタム テーマと拡張機能を使用して自分のエクスペリエンスを拡張できます。(CTP 2.0)
  - 組み込まれているサブスクリプションとリソースのブラウザーを使用して、Azure リソースを調べることができます。 (CTP 2.0)
  - SQL Server ビッグ データ クラスターを使用するシナリオをサポートします。 (CTP 2.0)
  
  > [!TIP]
  > Azure Data Studio の最新の機能向上については、「[Azure Data Studio のリリース ノート](../azure-data-studio/release-notes-azure-data-studio.md)」をご覧ください。

- [**SQL Server Management Studio (SSMS) 18.0 (プレビュー)** ](../ssms/sql-server-management-studio-ssms.md): [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]をサポートします。

  - SSMS から Azure Data Studio を起動します。 (CTP 2.3)
  - セキュリティで保護されたエンクレーブが設定された Always Encrypted をサポートします。 (CTP 2.0)
  - ダウンロード サイズが小さくなりました。 (CTP 2.0)
  - Visual Studio 2017 Isolated Shell に基づくようになりました。 (CTP 2.0)
  - 完全な一覧については、[SSMS の変更ログ](../ssms/release-notes-ssms.md)に関する記事をご覧ください。 (CTP 2.0)

- [**SQL Server PowerShell モジュール**](http://www.powershellgallery.com/packages/SqlServer/21.1.18080): SQL Server の開発者、管理者、BI 専門家は、SqlServer PowerShell モジュールを使用して、データベースの配置とサーバーの管理を自動化できます。

  - 21.0 から 21.1 にアップグレードして SMO v150 をサポートします。
  - AS/IS/RS グループを表示するように SQL Server プロバイダー (SQLRegistration) が更新されました。
  - SQL Server 2014 を対象にしたときの `New-SqlAvailabilityGroup` コマンドレットの問題を修正しました。
  - `Set-SqlAvailabilityReplica` と `New-SqlAvailabilityReplica` に `–LoadBalancedReadOnlyRoutingList` パラメーターが追加されました。
  - Azure Analysis Services に対して `AnalysisService` からキャッシュされたログイン トークンを使用するように `Login-AzureAsAccount` コマンドレットが更新されました。

### <a id="ssas"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS) 

#### <a name="online-attach-ctp32"></a>オンラインのアタッチ (CTP 3.2)

CTP 3.2 では、オンライン操作として表形式モデルをアタッチする機能が導入されました。 オンラインのアタッチは、オンプレミスのクエリ スケールアウト環境で読み取り専用レプリカを同期するために使用できます。オンラインのアタッチ操作を実行するには、Attach XMLA コマンドの **AllowOverwrite** オプションを使用します。 

```xmla
<Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine"> 
  <Folder>C:\Program Files\Microsoft SQL Server\MSAS15\OLAP\Data\AdventureWorks.0.db\</Folder> 
  <AllowOverwrite>True</AllowOverwrite> 
</Attach> 
```

新しいバージョンの読み込み時に古いバージョンをオンライン状態に保つには、この操作で "*モデルのメモリを 2 倍にする*" ことが必要になる場合があります。 

一般的な使用パターンは次のとおりです。 

1. DB1 (バージョン 1) は既に読み取り専用サーバー B にアタッチされています。 

2. DB1 (バージョン 2) は書き込みサーバー A 上で処理されます。 

3. DB1 (バージョン 2) はデタッチされ、サーバー B からアクセスできる場所に配置されます (共有の場所を介して、または robocopy などを使用して)。 

4. AllowOverwrite=True を指定した<Attach>コマンドは、新しい場所の DB1 (バージョン 2) を使用してサーバー B 上で実行されます。 

この機能を使用しない場合、管理者はまずデータベースをデタッチしてから、新しいバージョンのデータベースをアタッチする必要があります。 これにより、ダウンタイムが発生してユーザーがデータベースを使用できなくなったり、それに対するクエリが失敗したりします。 

この新しいフラグを指定すると、データベースのバージョン 1 は、ダウンタイムなしで、同じトランザクション内で原子的に削除されます。 ただし、両方のデータベースが同時にメモリに読み込まれるという代償は伴います。 


#### <a name="many-to-many-ctp24"></a>表形式モデルの多対多リレーションシップ (CTP 2.4)

この機能では、両列が一意でない場合の多対多リレーションシップが許可されます。 ディメンションのキー列よりも高い粒度でディメンションとファクト テーブル間のリレーションシップを定義できます。 これにより、ディメンション テーブルを正規化せずに済み、結果のモデルが、論理的にグループ化された列を持つより少数のテーブルのものとなるので、ユーザー エクスペリエンスを向上できます。 この CTP 2.4 リリースでは、多対他リレーションシップはエンジンに限定された機能です。 

多対多リレーションシップでは、モデルは 1470 互換性レベルである必要があり、これは現在 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 以降でのみサポートされています。 この CTP 2.4 リリースでは、多対多リレーションシップは、Tabular Object Model (TOM) API、テーブル モデル スクリプト言語 (TMSL)、およびオープン ソースの表形式エディター ツールを使用して作成できます。 SQL Server Data Tools (SSDT) でのサポートは、将来のリリースとドキュメントで組み込まれます。 この機能および他の CTP 機能のリリースに関する追加情報は、Analysis Services のブログで提供されます。

#### <a name="property-ctp24"></a>リソース ガバナンスのメモリ設定 (CTP 2.4)

ここで説明するメモリ設定は、Azure Analysis Service で既に使用できます。 CTP 2.4 以降では、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の Analysis Services でもサポートされるようになりました。 

- **Memory\QueryMemoryLimit**: このメモリ プロパティは、モデルに送信された DAX クエリによって構築されたメモリ スプールを制限するために使用できます。 
- **DbpropMsmdRequestMemoryLimit**: この XMLA プロパティは、接続用の Memory\QueryMemoryLimit サーバー プロパティ値をオーバーライドするために使用できます。
- **OLAP\Query\RowsetSerializationLimit**: このサーバー プロパティは、行セットで返される行数を制限するために使用でき、サーバー リソースが広範なデータ エクスポートの用途に使用されるのを防ぎます。 このプロパティは、DAX クエリと MDX クエリの両方に適用されます。

これらのプロパティは、SQL Server Management Studio (SSMS) の最新バージョンを使用して設定できます。 この機能の追加情報は、Analysis Services のブログで提供します。

#### <a name="calc-ctp24"></a>テーブル モデルでの計算グループ (CTP 2.3) 

計算グループは、タイム インテリジェンスのような、同じ計算を使用するメジャーの数が増加する可能性のある複雑なモデルで一般的な問題に対処します。 計算グループは、レポート クライアントでは 1 つの列を含むテーブルとして示されます。 列内の各値は、メジャーに適用できる再利用可能な計算または計算アイテムを表します。  

計算グループは任意の数の計算アイテムを保持できます。 各計算アイテムは DAX 式によって定義されます。 計算グループを操作するため、次の 3 つの新しい DAX 関数が導入されています。 

- `SELECTEDMEASURE()` - 現在コンテキスト内にあるメジャーへの参照を返します。  

- `SELECTEDMEASURENAME()` - 現在コンテキスト内にあるメジャーの名前を含む文字列を返します。  

- `ISSELECTEDMEASURE(M1, M2, …)` - 現在コンテキスト内にあるメジャーが引数として指定されているメジャーの 1 つかどうかを示すブール値を返します。

新しい DAX 関数に加えて、次の 2 つの新しい動的管理ビューが導入されています。

- `TMSCHEMA_CALCULATION_GROUPS`  
- `TMSCHEMA_CALCULATION_ITEMS`  

##### <a name="limitations-in-this-release"></a>このリリースの制限:

- `ALLSELECTED DAX` 関数はまだサポートされません。
- 計算グループ テーブルで定義された行レベル セキュリティは、まだサポートされていません。
- 計算グループ テーブルで定義されたオブジェクト レベル セキュリティは、まだサポートされていません。
- 計算アイテムを参照する DetailsRows 式は、まだサポートされていません。
- MDX はまだサポートされていません。

##### <a name="known-issues-in-this-release"></a>このリリースの既知の問題:

- モデルに計算グループが存在する場合、メジャーがバリアント データ型を返す場合があります。これにより、メジャーを参照する計算済みの列と表の更新が失敗します。

##### <a name="compatibility-level"></a>互換性レベル

計算グループでは、モデルは 1470 互換性レベルである必要があり、これは現在 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 以降でのみサポートされています。 現時点では、計算グループは、Tabular Object Model (TOM) API、テーブル モデル スクリプト言語 (TMSL)、およびオープン ソースの表形式エディター ツールを使用することによって作成できます。 SQL Server Data Tools (SSDT) でのサポートは、将来のリリースとドキュメントで組み込まれます。 この機能および他の CTP 機能のリリースに関する追加情報は、Analysis Services のブログで提供されます。

## <a name="see-also"></a>参照

- [`SqlServer` PowerShell モジュール](https://www.powershellgallery.com/packages/Sqlserver)
- [SQL Server PowerShell ドキュメント](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>次の手順

- [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] リリース ノート](sql-server-ver15-release-notes.md)。

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]:テクニカル ホワイト ペーパー](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />2018 年 9 月に公開されました。 Windows、Linux、Docker コンテナー向けの Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 に適用されます。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
