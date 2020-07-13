---
title: '&#39;の新機能 (データベースエンジン) |Microsoft Docs'
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ae3b565f858c383775b4fcccfac236c316fcfa4e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927433"
---
# <a name="what39s-new-database-engine"></a>新機能 (データベースエンジン)&#39;
  この最新リリースの [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]には、データ ストレージ システムを設計、開発、および管理する設計者、開発者、および管理者の能力や生産性を向上させる、以下のような新機能や機能強化が導入されています。 [!INCLUDE[ssDE](../includes/ssde-md.md)]の機能が強化された分野は以下のとおりです。  
  
##  <a name="database-engine-feature-enhancements"></a><a name="Feature"></a>データベースエンジン機能の機能強化  
  
###  <a name="memory-optimized-tables"></a><a name="MemoryOpt"></a>メモリ最適化テーブル  
 インメモリ OLTP は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エンジンに統合されたメモリ最適化データベース エンジンです。 インメモリ OLTP は OLTP 向けに最適化されています。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
 
  
###  <a name="sql-server-data-files-in-azure"></a><a name="DataFiles"></a>Azure でのデータファイルの SQL Server  
 [Azure のデータファイルを SQL Server](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] azure blob として格納されているデータベースファイルのネイティブサポートが有効になります。 この機能を使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンプレミスまたは Azure の仮想マシンで実行されているデータベースを、Azure Blob Storage のデータ専用のストレージの場所として作成できます。  
  
  
###  <a name="host-a-sql-server-database-in-an-azure-virtual-machine"></a><a name="AzureVM"></a>Azure の仮想マシンで SQL Server データベースをホストする  
 Azure 仮想マシン[への SQL Server データベースのデプロイ](https://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx)ウィザードを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] azure 仮想マシン内ののインスタンスからデータベースをホストします。  
  
  
###  <a name="backup-and-restore-enhancements"></a><a name="Backup"></a>バックアップと復元の機能強化  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] には、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元に関する次の強化点が含まれています。  
  
-   **SQL Server Backup to URL**  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Backup to URL は [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] SP1 CU2 で導入され、[!INCLUDE[tsql](../includes/tsql-md.md)]、PowerShell、および SMO でのみサポートされています。 では、を使用して、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Azure Blob ストレージサービスに対してバックアップまたは復元を行うことができます。 バックアップ タスクとメンテナンス プランの両方で、この新しいオプションを使用できます。 詳細については、「 [SQL Server Management Studio でのバックアップタスクの使用](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS)」、「[メンテナンスプランウィザードを使用したバックアップ URL の SQL Server](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz)」、および「 [SQL Server Management Studio を使用した Azure storage からの復元](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS)」を参照してください。  
  
-   **Azure へのマネージバックアップの SQL Server**  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Backup to URL を基盤とした [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] は、データベースとログのバックアップを管理およびスケジュール設定するために [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が提供するサービスです。 このリリースでは、Azure storage へのバックアップのみがサポートされています。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] をデータベースとインスタンス レベルの両方で構成して、データベース レベルの詳細な制御とインスタンス レベルの自動化の両方を達成することもできます。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、オンプレミスで実行されているインスタンスと、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Azure 仮想マシン上で実行されているインスタンスで構成できます。 Azure 仮想マシンで実行されているインスタンスでは、この方法をお勧め [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] します。 詳細については、「 [Azure へのマネージバックアップの SQL Server](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。  
  
-   **バックアップの暗号化**  
  
     バックアップ操作中にバックアップ ファイルを暗号化する方法を選択できるようになりました。  AES 128、AES 192、AES 256、Triple DES を含むいくつかの暗号化アルゴリズムがサポートされています。 バックアップ中に暗号化を実行するには、証明書または非対称キーを使用する必要があります。 詳細については、「 [バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)」をご覧ください。  
  
  
###  <a name="new-design-for-cardinality-estimation"></a><a name="CE"></a>カーディナリティの推定の新しいデザイン  
 カーディナリティ推定ロジックをカーディナリティ推定機能と呼びますが、クエリ プランの品質を向上させ、その結果、クエリのパフォーマンスを向上させる目的で、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] でこの機能を再設計しました。 新しいカーディナリティ推定機能には、現在の OLTP ワークロードとデータ ウェアハウス ワークロードで適切に機能する想定とアルゴリズムが組み込まれています。 この機能は、現在のワークロードを対象とするカーディナリティ推定に関する詳細な調査、および SQL Server のカーディナリティ推定機能を向上させるための過去 15 年にわたる研究を土台としています。 お客様からのフィードバックによると、大半のクエリは今回の変更によって性能が向上するか、何も変化しないこと、一方で、少数のクエリは以前のカーディナリティ推定機能と比較すると性能が低下する可能性があることが示されています。 パフォーマンスのチューニングとテストの推奨事項については、「[カーディナリティの推定 &#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md)」を参照してください。  
   
  
###  <a name="delayed-durability"></a><a name="Durability"></a>遅延持続性  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] には、一部またはすべてのトランザクションを遅延持続性トランザクションとして指定することにより待機時間を短縮する機能が導入されています。 遅延持続性トランザクションがクライアントに制御を返した後、トランザクション ログ レコードがディスクに書き込まれます。 持続性は、データベース レベル、COMMIT レベル、または ATOMIC ブロック レベルで管理できます。  
  
 詳細については、「[トランザクションの持続性の制御](../relational-databases/logs/control-transaction-durability.md)」を参照してください。  
  
  
###  <a name="alwayson-enhancements"></a><a name="AlwaysOn"></a>AlwaysOn の機能強化  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では、AlwaysOn フェールオーバー クラスター インスタンスと AlwaysOn 可用性グループが次のように強化されています。  
  
-   Azure のレプリカ追加ウィザードにより、AlwaysOn 可用性グループ用の複合ソリューションを容易に作成できます。 詳細については、「 [Azure のレプリカ追加ウィザードを使用して &#40;SQL Server&#41;](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md)」を参照してください。  
  
-   セカンダリ レプリカの最大数は、4 から 8 に増えています。  
  
-   プライマリ レプリカから切断された場合やクラスター クォーラムが存在しない場合でも、読み取り可能なセカンダリ レプリカを、読み取りワークロードに対して引き続き使用できるようになりました。  
  
-   フェールオーバー クラスター インスタンス (FCI) では、クラスターの共有ボリューム (CSV) を、クラスターの共有ディスクとして使用できます。 詳細については、「 [Always On フェールオーバークラスターインスタンス](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。  
  
-   新しいシステム関数、 [sys. fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql)、および新しい DMV、 [dm_io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql)を使用できます。  
  
-   次の Dmv が拡張され、FCI 情報が返されるようになりました: [dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)、 [sys. dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)、および[sys. dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)。  
  
  
###  <a name="partition-switching-and-indexing"></a><a name="OIR"></a>パーティションの切り替えとインデックス作成  
 パーティション テーブルの個々のパーティションを再構築できるようになりました。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。  
   
  
###  <a name="managing-the-lock-priority-of-online-operations"></a><a name="Lock"></a>オンライン操作のロック優先順位の管理  
 `ONLINE = ON` オプションには、再構築プロセスで必要なロックを待機する時間を指定できるようにする `WAIT_AT_LOW_PRIORITY` オプションが追加されました。 `WAIT_AT_LOW_PRIORITY` オプションを使用すると、当該の再構築ステートメントに関連するブロック プロセスの終了を構成こともできます。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」および「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。 新しい種類のロック状態に関するトラブルシューティングについては、「 [sys. dm_tran_locks &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) 」と「 [dm_os_wait_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)」を参照してください。  
 
  
###  <a name="columnstore-indexes"></a><a name="CCI"></a>列ストアインデックス  
 次の新機能は、列のインデックスで使用できます。  
  
-   **クラスター化列ストア インデックス**  
  
     クラスター化列ストア インデックスは、主に一括読み込みと読み取り専用クエリを実行するデータ ウェアハウスのワークロードでデータ圧縮とクエリ パフォーマンスを向上させるために使用します。 クラスター化列ストア インデックスは更新可能であるため、ワークロードは多くの挿入、更新、および削除操作を実行できます。 詳細については、「[列ストアインデックスの説明](../relational-databases/indexes/columnstore-indexes-described.md)」と「[クラスター化列ストアインデックスの使用](../relational-databases/indexes/indexes.md)」を参照してください。  
  
-   **ヲ**  
  
     SHOWPLAN には、列ストア インデックスに関する情報が表示されます。 **は**プロパティと**actualexecutionmode**プロパティには、**バッチ**または**行**の2つの有効な値があります。  **ストレージ**プロパティには、**行ストア**と**列ストア**という2つの値があります。  
  
-   **アーカイブデータの圧縮**  
  
     インデックスの変更...REBUILD には、列ストアインデックスの指定されたパーティションをさらに圧縮する新しい COLUMNSTORE_ARCHIVE データ圧縮オプションがあります。 保存用や、データ ストレージのサイズを減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用します。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。  
   
  
###  <a name="buffer-pool-extension"></a><a name="Buffer"></a>バッファープール拡張機能  
 [バッファープール拡張](configure-windows/buffer-pool-extension.md)は、ソリッドステートドライブ (SSD) を不揮発性ランダムアクセスメモリ (NvRAM) 拡張としてバッファープールにシームレスに統合することで、 [!INCLUDE[ssDE](../includes/ssde-md.md)] i/o スループットを大幅に向上させます。  
   
  
###  <a name="incremental-statistics"></a><a name="Stats"></a>増分統計  
 CREATE STATISTICS と関連する統計ステートメントでは、INCREMENTAL オプションを使用してパーティションごとの統計を作成することが許可されるようになりました。 関連するステートメントは増分統計を許可または報告します。 影響を受ける構文には、UPDATE STATISTICS、sp_createstats、CREATE INDEX、ALTER INDEX、ALTER DATABASE SET オプション、DATABASEPROPERTYEX、sys. databases、および sys. stats があります。詳細については、「 [CREATE STATISTICS &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)」を参照してください。  
  
  
###  <a name="resource-governor-enhancements-for-physical-io-control"></a><a name="RG"></a>物理 IO 制御の Resource Governor の機能強化  
 リソース ガバナーを使用すると、着信アプリケーション要求がリソース プール内で使用できる CPU、物理 IO、およびメモリの量に制限を指定できます。 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] で、新しい MIN_IOPS_PER_VOLUME 設定と MAX_IOPS_PER_VOLUME 設定を使用すると、特定のリソース プールのユーザー スレッドに対して発行された物理 IO を制御できます。 詳細については、「 [Resource Governor リソースプール](../relational-databases/resource-governor/resource-governor-resource-pool.md)」と「 [CREATE Resource pool &#40;transact-sql&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)」を参照してください。  
  
 ALTER RESOURCE GOVENOR の MAX_OUTSTANDING_IO_PER_VOLUME 設定は、ディスク ボリュームごとに未処理の I/O 操作の最大数を設定します。 この設定を使用して、ディスク ボリュームの IO の特性に合わせて IO リソース管理を調整することや、SQL Server インスタンスの境界で発行される IO の数を制限することができます。 詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)」を参照してください。  
  
  
###  <a name="online-index-operation-event-class"></a><a name="OnlineEvent"></a>Online Index Operation イベントクラス  
 Online index operation イベントクラスの進行状況レポートには、 **PartitionId**と**partitionnumber**という2つの新しいデータ列が追加されました。 詳細については、「 [Progress Report: Online Index Operation イベントクラス](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md)」を参照してください。  
  
  
###  <a name="database-compatibility-level"></a><a name="Compat"></a>データベース互換性レベル  
 互換性レベル 90 は、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では無効です。 詳細については、「 [ALTER Database Compatibility Level &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) 」を参照してください。  
  
##  <a name="transact-sql-enhancements"></a><a name="TSQL"></a>Transact-sql の機能強化  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>CLUSTERED および NONCLUSTERED のインライン指定  
 ディスク ベース テーブルに対する `CLUSTERED` および `NONCLUSTERED` インデックスのインライン指定が許可されるようになりました。 インライン インデックスを含むテーブルを作成することは、テーブルの作成ステートメントに続いて、対応する `CREATE INDEX` ステートメントを発行することと同じです。 付加列とフィルター条件は、インライン インデックスではサポートされていません。  
  
### <a name="select--into"></a>選択...ドラッグ  
 `SELECT ... INTO` ステートメントは改善され、並行して実行できるようになりました。 データベース互換性レベルを 110 以上に設定する必要があります。  
  
### <a name="tsql-enhancements-for-in-memory-oltp"></a>[!INCLUDE[tsql](../includes/tsql-md.md)] でのインメモリ OLTP の強化  
 インメモリ OLTP をサポートするための変更点の詳細については [!INCLUDE[tsql](../includes/tsql-md.md)] 、「 [Transact-sql によるインメモリ Oltp のサポート](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)」を参照してください。  
  
  
##  <a name="system-view-enhancements"></a><a name="SystemTable"></a>システムビューの機能強化  
  
### <a name="sysxml_indexes"></a>sys.xml_indexes  
 [sys.xml_indexes &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql)には `xml_index_type` 、、、およびの3つの新しい列があり `xml_index_type_description` `path_id` ます。  
  
### <a name="sysdm_exec_query_profiles"></a>sys.dm_exec_query_profiles  
 [dm_exec_query_profiles &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql)は、クエリの実行中にリアルタイムのクエリの進行状況を監視します。  
  
### <a name="syscolumn_store_row_groups"></a>sys.column_store_row_groups  
 [column_store_row_groups &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)では、クラスター化列ストアインデックス情報がセグメント単位で提供されるため、管理者はシステム管理を決定できます。  
  
### <a name="sysdatabases"></a>sys.databases  
 [transact-sql&#41;の &#40;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)には `is_auto_create_stats_incremental_on` 、、 `is_query_store_on` 、およびの3つの新しい列 `resource_pool_id` があります。  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>インメモリ OLTP に関連するシステム ビューの強化  
 インメモリ OLTP をサポートするシステムビューの機能強化の詳細については、「[インメモリ oltp のシステムビュー、ストアドプロシージャ、dmv、および待機の種類](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)」を参照してください。  
   
  
##  <a name="security-enhancements"></a><a name="Security"></a>セキュリティの強化  
  
### <a name="connect-any-database-permission"></a>CONNECT ANY DATABASE 権限  
 新しいサーバー レベル権限です。 既存のあらゆるデータベースと今後作成されるすべての新規データベースに接続する必要のあるログインに、**CONNECT ANY DATABASE** を付与します。 接続以外の権限はどのデータベースにおいても一切付与されません。 **SELECT ALL USER SECURABLES**またはを組み合わせて `VIEW SERVER STATE` 、のインスタンス上のすべてのデータまたはすべてのデータベースの状態を監査プロセスで表示できるようにし [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。  
  
### <a name="impersonate-any-login-permission"></a>IMPERSONATE ANY LOGIN 権限  
 新しいサーバー レベル権限です。 この権限が付与されていると、中間層プロセスがデータベースに接続するときに、そこに接続するクライアントのアカウントの権限を借用できます。 この権限が拒否されていると、高い特権を持つログインが他のログインの権限を借用するのをブロックできます。 たとえば、**CONTROL SERVER** 権限を持つログインが他のログインの権限を借用するのをブロックできます。  
  
### <a name="select-all-user-securables-permission"></a>SELECT ALL USER SECURABLES 権限  
 新しいサーバー レベル権限です。 付与されていると、監査担当者などログインが、ユーザーが接続できるすべてのデータベースのデータを表示できます。  
  
  
##  <a name="deployment-enhancements"></a><a name="Deployment"></a>展開の機能強化  
### <a name="azure-vm"></a>Azure VM
[SQL Server データベースを Microsoft Azure 仮想マシンにデプロイ](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)すると、Azure VM へのデータベースのデプロイが可能になり [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。  

### <a name="refs"></a>ReFS
ReFS でのデータベースの配置がサポートされるようになりました。   
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
