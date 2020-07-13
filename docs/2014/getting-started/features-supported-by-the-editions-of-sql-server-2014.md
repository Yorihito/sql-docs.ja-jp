---
title: SQL Server 2014 | の各エディションがサポートする機能Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
author: rothja
ms.author: jroth
ms.openlocfilehash: 93555bbbc6c7a10955e8fc869f6ddadc38572830
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927133"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>SQL Server 2014 の各エディションがサポートする機能


  このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のさまざまなエディションでサポートされる機能の詳細について説明します。 

 > **注:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は、180日間の試用期間中、評価版でご利用いただけます。 詳細については、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [試用版ソフトウェアの Web サイト](https://go.microsoft.com/fwlink/?LinkId=190955)を参照してください。  
> 
> **注:** 評価版と Developer edition でサポートされている機能については、Enterprise の機能セットを参照してください [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。  
  
 各 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テクノロジの表に移動するには、それぞれのリンクをクリックしてください。  
  
 [クロスボックスのスケールの制限](#CrossBoxScale)  
  
 [高可用性](#High_availability)  
  
 [スケーラビリティとパフォーマンス](#Scalability)  
  
 [Security](#Enterprise_security)  
  
 [レプリケーション](#Replication)  
  
 [管理ツール](#Mgmt_Tools)  
  
 [RDBMS の管理の容易性](#RDBMS_mgmt)  
  
 [開発ツール](#Dev_tools)  
  
 [プログラミング](#Programmability)  
  
 [統合サービス](#SSIS)  
  
 [Integration Services – 拡張アダプター](#SSIS_AA)  
  
 [Integration Services – 詳細な変換](#SSIS_AT)  
  
 [マスター データ サービス](#MDS)  
  
 [データウェアハウス](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [BI セマンティック モデル (多次元)](#BISemModel_multi)  
  
 [BI セマンティック モデル (テーブル)](#BISemModel_tabular)  
  
 [PowerPivot for SharePoint](#PowerPivot)  
  
 [データ マイニング](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Business Intelligence クライアント](#BIClients)  
  
 [空間サービスとロケーションサービス](#Spatial)  
  
 [その他のデータベース サービス](#Add_DBServices)  
  
 [その他のコンポーネント](#Other_Components)  
  
##  <a name="cross-box-scale-limits"></a><a name="CrossBoxScale"></a>クロスボックスのスケールの制限  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|1つのインスタンスで使用される最大計算容量 ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースエンジン)<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 16 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
|1つのインスタンスで使用される最大計算容量 (Analysis Services、Reporting Services) <sup>1</sup>|オペレーティング システムの最大容量|オペレーティング システムの最大容量|4 ソケットまたは 16 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジンのインスタンスごと)|オペレーティング システムの最大容量|128 GB|128 GB|64 GB|1 GB|1 GB|1 GB|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスごと)|オペレーティング システムの最大容量|オペレーティング システムの最大容量|64 GB|該当なし|該当なし|該当なし|該当なし|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のインスタンスごと)|オペレーティング システムの最大容量|オペレーティング システムの最大容量|64 GB|64 GB|4 GB|該当なし|該当なし|  
|リレーショナル データベースの最大サイズ|524 PB|524 PB|524 PB|524 PB|10 GB|10 GB|10 GB|  
  
 <sup>1</sup> Enterprise Edition with Server および Client Access LICENSE (CAL) に基づくライセンス (新しい契約では利用できません) は、インスタンスあたり最大20コアに制限されてい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。 コアベースのサーバー ライセンス モデルでは、制限はありません。 詳細については、「 [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)」を参照してください。  
  
##  <a name="high-availability"></a><a name="High_availability"></a>高可用性  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Server Core サポート<sup>1</sup>|[はい]|はい|はい|はい|はい|はい|はい|  
|ログ配布|[はい]|はい|はい|はい||||  
|データベース ミラーリング|Yes|可 (安全性レベルが FULL の場合のみ)|可 (安全性レベルが FULL の場合のみ)|ミラーリング監視のみ|ミラーリング監視のみ|ミラーリング監視のみ|ミラーリング監視のみ|  
|バックアップ圧縮|[はい]|はい|はい|||||  
|データベース スナップショット|Yes|||||||  
|AlwaysOn フェールオーバー クラスター インスタンス|可 (ノード サポート: オペレーティング システムの最大容量)|可 (ノード サポート: 2)|可 (ノード サポート: 2)|||||  
|AlwaysOn 可用性グループ|可 (2 個の同期セカンダリ レプリカを含む最大 8 個のセカンダリ レプリカ)|||||||  
|接続ディレクター|Yes|||||||  
|オンライン ページおよびファイルの復元|Yes|||||||  
|オンラインのインデックス構築|Yes|||||||  
|オンラインのスキーマ変更|Yes|||||||  
|高速復旧|Yes|||||||  
|ミラー化バックアップ|Yes|||||||  
|ホットアドメモリと CPU<sup>2</sup>|Yes|||||||  
|データベース復旧アドバイザー|[はい]|はい|はい|はい|はい|はい|はい|  
|暗号化されたバックアップ|[はい]|はい|はい|||||  
|スマート バックアップ|[はい]|はい|はい|いいえ||||  
  
 <sup>1</sup>Server Core へののインストールの詳細につい [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ては、「 [Install SQL Server 2014 On server core](../database-engine/install-windows/install-sql-server-on-server-core.md)」を参照してください。  
  
 <sup>2</sup>この機能は、64ビットのでのみ使用でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。  
  
##  <a name="scalability-and-performance"></a><a name="Scalability"></a>スケーラビリティとパフォーマンス  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|複数インスタンスのサポート|50|50|50|50|50|50|50|  
|テーブルとインデックスのパーティション分割|Yes|||||||  
|データ圧縮|はい|||||||  
|[リソース ガバナー]|はい|||||||  
|パーティション テーブルの並列処理|Yes|||||||  
|複数の Filestream コンテナー|Yes|||||||  
|NUMA 対応のラージ ページ メモリとバッファー配列の割り当て|Yes|||||||  
|バッファープール拡張<sup>1</sup>|[はい]|はい|はい|||||  
|IO リソース管理|Yes|||||||  
|インメモリ OLTP <sup>1</sup>|Yes|||||||  
|遅延持続性|[はい]|はい|はい|はい|はい|はい|はい|  
  
 <sup>1</sup>この機能は64ビットのみで使用でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。  
  
##  <a name="security"></a><a name="Enterprise_security"></a> セキュリティ  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|基本的な監査|[はい]|はい|はい|はい|はい|はい|はい|  
|詳細な監査|はい|||||||  
|透過的なデータベースの暗号化|はい|||||||  
|拡張キー管理|Yes|||||||  
|ユーザー定義ロール|[はい]|はい|はい|はい|はい|はい|はい|  
|包含データベース|[はい]|はい|はい|はい|はい|はい|はい|  
|バックアップの暗号化|[はい]|はい|はい|||||  
  
##  <a name="replication"></a><a name="Replication"></a> レプリケーション  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 変更の追跡|[はい]|はい|はい|はい|はい|はい|はい|  
|マージ レプリケーション|[はい]|はい|はい|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|  
|トランザクション レプリケーション|[はい]|はい|はい|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|  
|スナップショット レプリケーション|[はい]|はい|はい|可 (サブスクライバーのみ)|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|はい (サブスクライバーのみ)|  
|異種サブスクライバー|[はい]|はい|はい|||||  
|Oracle パブリッシュ|Yes|||||||  
|ピア ツー ピア トランザクション レプリケーション|Yes|||||||  
  
##  <a name="management-tools"></a><a name="Mgmt_Tools"></a>管理ツール  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SQL 管理オブジェクト (SMO)|はい|はい|はい|はい|はい|はい|はい|  
|SQL 構成マネージャー|はい|はい|はい|はい|はい|はい|はい|  
|SQL CMD (コマンド プロンプト ツール)|はい|はい|はい|はい|はい|はい|はい|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio|はい|はい|はい|はい|はい|はい||  
|分散再生 - 管理ツール|はい|はい|はい|はい|はい|はい||  
|分散再生 - クライアント|はい|いいえ|はい|はい||||  
|分散再生 - コントローラー|可 (Enterprise では最大 16 クライアントのサポート、Developer では 1 クライアントのみサポート)|No|可 (1 クライアントのサポートのみ)|可 (1 クライアントのサポートのみ)||||  
|SQL Profiler|はい|はい|はい|いいえ<sup>2</sup>|いいえ<sup>2</sup>|いいえ<sup>2</sup>|いいえ<sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント|はい|はい|はい|はい||||  
|Microsoft System Center Operations Manager 管理パック|はい|はい|はい|はい||||  
|データベース チューニング アドバイザー (DTA)|はい|はい|○<sup>3</sup>|○<sup>3</sup>||||  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AZURE VM にデータベースを配置ウィザード|はい|はい|はい|はい|はい|はい|はい|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Azure のデータファイル|はい|はい|はい|はい|はい|はい|はい|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Web、 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 、 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] With Tools、および [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard edition と Enterprise edition を使用してプロファイルでき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。  
  
 <sup>3</sup>チューニングは Standard edition 機能でのみ有効です。  
  
##  <a name="rdbms-manageability"></a><a name="RDBMS_mgmt"></a>RDBMS の管理の容易性  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|ユーザー インスタンス|||||はい|はい|Yes|  
|LocalDB|||||はい|Yes||  
|専用管理者接続|はい|はい|はい|Yes|可 (トレース フラグでサポートされている)|可 (トレース フラグでサポートされている)|可 (トレース フラグでサポートされている)|  
|PowerShell スクリプティングのサポート|はい|はい|はい|はい|はい|はい|Yes|  
|SysPrep サポート<sup>1</sup>|はい|はい|はい|はい|はい|はい|Yes|  
|データ層アプリケーションコンポーネントの操作 (抽出、配置、アップグレード、削除) のサポート|はい|はい|はい|はい|はい|はい|はい|  
|ポリシー オートメーション (変更時とスケジュールに基づいて確認)|はい|はい|はい|Yes||||  
|パフォーマンス データ コレクター|はい|はい|はい|Yes||||  
|複数インスタンス管理でマネージド インスタンスとして登録できる|はい|はい|はい|Yes||||  
|標準的なパフォーマンス レポート|はい|はい|はい|Yes||||  
|プラン ガイドおよびプラン ガイドの固定計画|はい|はい|はい|Yes||||  
|NOEXPAND ヒントを使用したインデックス付きビューの直接クエリ|はい|はい|はい|Yes||||  
|インデックス付きビューの自動メンテナンス|はい|はい|はい|Yes||||  
|分散パーティション ビュー|はい|部分的。 分散パーティション ビューは更新できない|部分的。 分散パーティション ビューは更新できない|部分的。 分散パーティション ビューは更新できない|部分的。 分散パーティション ビューは更新できない|部分的。 分散パーティション ビューは更新できない|部分的。 分散パーティション ビューは更新できない|  
|並列インデックス操作|Yes|||||||  
|クエリ オプティマイザーによる自動的なインデックス付きのビュー使用|Yes|||||||  
|並列整合性チェック|はい|||||||  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティ コントロール ポイント|Yes|||||||  
|包含データベース|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|バッファープール拡張<sup>2</sup>|[はい]|[はい]|Yes|||||  
  
 <sup>1</sup> 詳細については、「 [SysPrep を使用した SQL Server のインストールに関する注意点](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」を参照してください。  
  
 <sup>2</sup>この機能は、64ビットのでのみ使用でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。  
  
##  <a name="development-tools"></a><a name="Dev_tools"></a>開発ツール  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio との統合|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|Intellisense ([!INCLUDE[tsql](../includes/tsql-md.md)] および MDX)|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|[はい]|[はい]|[はい]|[はい]|Yes|||  
|SQL クエリの編集およびデザインツール<sup>1</sup>|[はい]|[はい]|Yes|||||  
|バージョン管理のサポート<sup>1</sup>|[はい]|[はい]|Yes|||||  
|MDX 編集、デバッグ、およびデザインツール<sup>1</sup>|[はい]|[はい]|Yes|||||  
  
 <sup>1</sup>この機能は、64ビット版の Standard edition では使用できません。  
  
##  <a name="programmability"></a><a name="Programmability"></a> Programmability  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|共通言語ランタイム (CLR) 統合|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|ネイティブ XML サポート|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|はい|  
|XML インデックスの作成|はい|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|UPSERT 機能をマージ &|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|FILESTREAM のサポート|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|FileTable|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|日付および時刻データ型|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|国際化サポート|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|はい|  
|フルテキストおよびセマンティック検索|[はい]|[はい]|[はい]|[はい]|Yes|||  
|クエリ内の言語指定|はい|[はい]|[はい]|[はい]|はい|||  
|Service Broker (メッセージング)|はい|[はい]|Yes|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|  
|[!INCLUDE[tsql](../includes/tsql-md.md)] エンドポイント|[はい]|[はい]|[はい]|Yes||||  
  
##  <a name="integration-services"></a><a name="SSIS"></a> Integration Services  
  
|機能|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|組み込みのデータ ソース コネクタ|[はい]|[はい]|[はい]|[はい]|[はい]|[はい]|Yes|  
|SSIS デザイナーおよびランタイム|[はい]|[はい]|Yes|||||  
|基本的な変換|[はい]|[はい]|Yes|||||  
|基本的なデータ プロファイリング ツール|[はい]|[はい]|Yes|||||  
|Attunity の Change Data Capture Service for Oracle|Yes|||||||  
|Attunity の Change Data Capture Designer for Oracle|Yes|||||||  
  
###  <a name="integration-services---advanced-adapters"></a><a name="SSIS_AA"></a>Integration Services-高度なアダプター  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|高パフォーマンスの Oracle 変換先|Yes|||||||  
|高パフォーマンスの Teradata 変換先|Yes|||||||  
|SAP BW 変換元と変換先|Yes|||||||  
|データ マイニング モデル トレーニング変換先アダプター|Yes|||||||  
|ディメンション処理の変換先アダプター|Yes|||||||  
|パーティション処理の変換先アダプター|Yes|||||||  
|Attunity 変更データ キャプチャ コンポーネント|Yes|||||||  
|Attunity ODBC (Open Database Connectivity) 接続|Yes|||||||  
  
###  <a name="integration-services---advanced-transforms"></a><a name="SSIS_AT"></a>Integration Services-高度な変換  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|永続性 (高パフォーマンス) 参照|Yes|||||||  
|データ マイニング クエリ変換|Yes|||||||  
|あいまいグループ化変換とあいまい参照変換|Yes|||||||  
|用語抽出と用語参照変換|Yes|||||||  
  
##  <a name="master-data-services"></a><a name="MDS"></a>マスター データ サービス  
  
> [!NOTE]  
>  -   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は、64 ビット エディションの Business Intelligence と Enterprise でのみ使用できます。  
  
|機能|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース|はい|はい||||||  
|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーション|はい|はい||||||  
  
##  <a name="data-warehouse"></a><a name="Data_warehouse"></a>データウェアハウス  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|データベースを使用しないキューブ作成|はい|はい|はい|||||  
|自動生成ステージングとデータ ウェアハウス スキーマ|はい|はい|はい|||||  
|変更データ キャプチャ|Yes|||||||  
|スター結合クエリ最適化|Yes|||||||  
|スケーラブルな読み取り専用の Analysis Services 構成|Yes|||||||  
|パーティション テーブルとパーティション インデックスに対する並列クエリ処理|Yes|||||||  
|xVelocity メモリ最適化列ストア インデックス|Yes|||||||  
|グローバル バッチ集計|Yes|||||||  
  
##  <a name="analysis-services"></a><a name="SSAS"></a>Analysis Services  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|スケーラブルな共有データベース (アタッチ/デタッチ、読み取り専用データベース)|はい|はい||||||  
|データベースのバックアップ/復元、アタッチ/デタッチ|はい|はい|はい|||||  
|データベースの同期|はい|はい||||||  
|高可用性|はい|はい|はい|||||  
|プログラミング (AMO、ADOMD.Net、OLEDB、XML/A、ASSL)|はい|はい|はい|||||  
  
###  <a name="bi-semantic-model-multidimensional"></a><a name="BISemModel_multi"></a>BI セマンティックモデル (多次元)  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|準加法メジャー|はい|はい|不可<sup>1</sup>|||||  
|階層|はい|はい|はい|||||  
|KPI|はい|はい|はい|||||  
|パースペクティブ|はい|はい||||||  
|アクション|はい|はい|はい|||||  
|勘定科目インテリジェンス|はい|はい|はい|||||  
|タイム インテリジェンス|はい|はい|はい|||||  
|カスタム ロールアップ|はい|はい|はい|||||  
|キューブの書き戻し|はい|はい|はい|||||  
|ディメンションの書き戻し|はい|はい||||||  
|セルの書き戻し|はい|はい|はい|||||  
|ドリルスルー|はい|はい|はい|||||  
|高度な階層の種類 (親子、不規則階層)|はい|はい|はい|||||  
|高度なディメンション (参照ディメンション、多対多ディメンション)|はい|はい|はい|||||  
|リンク メジャーとディメンション|はい|はい||||||  
|翻訳|はい|はい|はい|||||  
|集計|はい|はい|はい|||||  
|複数パーティション|はい|はい|可 (3 つまで)|||||  
|プロアクティブ キャッシュ|はい|はい||||||  
|カスタム アセンブリ (ストアド プロシージャ)|はい|はい|はい|||||  
|MDX クエリおよびスクリプト|はい|はい|はい|||||  
|DAX クエリ|はい|はい||||||  
|ロールベースのセキュリティ モデル|はい|はい|はい|||||  
|ディメンションおよびセル レベルのセキュリティ|はい|はい|はい|||||  
|スケーラブルな文字列ストレージ|はい|はい|はい|||||  
|MOLAP、ROLAP、HOLAP ストレージ モード|はい|はい|はい|||||  
|バイナリおよび圧縮 XML の転送|はい|はい|はい|||||  
|プッシュモード処理|はい|はい||||||  
|直接書き戻し|はい|はい||||||  
|メジャー式|はい|はい||||||  
  
 <sup>1</sup>LastChild 準加法メジャーは standard edition でサポートされていますが、他の準加法メジャー (None、FirstChild、Firstchild でない、Lastchild、ByAccount など) はサポートされていません。 加法メジャー (Sum、Count、Min、Max など) や非加法メジャー (DistinctCount) はすべてのエディションでサポートされます。  
  
###  <a name="bi-semantic-model-tabular"></a><a name="BISemModel_tabular"></a>BI セマンティックモデル (テーブル)  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|階層|はい|はい||||||  
|KPI|はい|はい||||||  
|パースペクティブ|はい|はい||||||  
|翻訳|はい|はい||||||  
|DAX 計算、DAX クエリ、MDX クエリ|はい|はい||||||  
|行レベルのセキュリティ|はい|はい||||||  
|メジャー グループ|はい|はい||||||  
|In-Memory および DirectQuery ストレージ モード (テーブルのみ)|はい|はい||||||  
  
###  <a name="powerpivot-for-sharepoint"></a><a name="PowerPivot"></a> PowerPivot for SharePoint  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|共有サービス アーキテクチャに基づく SharePoint ファーム統合|はい|はい||||||  
|使用状況レポート|はい|はい||||||  
|状態の監視のルール|はい|はい||||||  
|PowerPivot ギャラリー|はい|はい||||||  
|PowerPivot のデータ更新|はい|はい||||||  
|PowerPivot データ フィード|はい|はい||||||  
  
###  <a name="data-mining"></a><a name="DataMining"></a>データマイニング  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|標準アルゴリズム|はい|はい|はい|||||  
|データ マイニング ツール (ウィザード、エディター、クエリ ビルダー)|はい|はい|はい|||||  
|クロス検証|はい|はい||||||  
|マイニング構造データのフィルター選択したサブセットのモデル|はい|はい||||||  
|時系列: ARTXP 法と ARIMA 法のカスタムな組み合わせ|はい|はい||||||  
|時系列: 新しいデータでの予測|はい|はい||||||  
|無制限の同時 DM クエリ|はい|はい||||||  
|データマイニングアルゴリズムの詳細な構成 & チューニングオプション|はい|はい||||||  
|プラグイン アルゴリズムのサポート|はい|はい||||||  
|並列モデル処理|はい|はい||||||  
|時系列: 系列のクロス予測|はい|はい||||||  
|アソシエーション ルールの無制限の属性|はい|はい||||||  
|シーケンス予測|はい|はい||||||  
|複数の Naïve Bayes の予測ターゲット、ニューラル ネットワーク、およびロジスティック回帰|はい|はい||||||  
  
##  <a name="reporting-services"></a><a name="Reporting"></a>Reporting Services  
  
###  <a name="reporting-services-features"></a><a name="Reporting_features"></a>Reporting Services 機能  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|サポートされているカタログ DB の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Standard 以上|Standard 以上|Standard 以上|Web|Express|||  
|サポートされているデータ ソースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|Web|Express|||  
|レポート サーバー|はい|はい|はい|はい|はい|||  
|レポート デザイナー|はい|はい|はい|はい|はい|||  
|レポート マネージャー|はい|はい|はい|はい|はい|||  
|ロール ベース セキュリティ|はい|はい|はい|はい|はい|||  
|ワード エクスポートおよびリッチ テキストのサポート|はい|はい|はい|はい|はい|||  
|強化されたゲージとグラフ|はい|はい|はい|はい|はい|||  
|Excel、PDF、およびイメージへのエクスポート|はい|はい|はい|はい|はい|||  
|カスタム認証|はい|はい|はい|はい|はい|||  
|データ フィードとしてのレポート|はい|はい|はい|はい|はい|||  
|モデルのサポート|はい|はい|はい|はい||||  
|ロールベースのセキュリティのカスタム ロールの作成|はい|はい|はい|||||  
|モデル アイテムのセキュリティ|はい|はい|はい|||||  
|無限クリック スルー|はい|はい|はい|||||  
|共有コンポーネント ライブラリ|はい|はい|はい|||||  
|電子メールおよびファイル共有のサブスクリプションとスケジュール設定|はい|はい|はい|||||  
|レポート履歴、実行スナップショット、およびキャッシュ|はい|はい|はい|||||  
|SharePoint 統合|はい|はい|はい|||||  
|リモートおよび非 SQL データ ソースのサポート<sup>1</sup>|はい|はい|はい|||||  
|データ ソース、配信およびレンダリング、RDCE の拡張性|はい|はい|はい|||||  
|データ ドリブン レポート サブスクリプション|はい|はい||||||  
|スケール アウト配置 (Web ファーム)|はい|はい||||||  
|警告<sup>2</sup>|はい|はい||||||  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|はい|はい||||||  
  
 <sup>1</sup>でサポートされるデータソースの詳細につい [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] ては、「 [REPORTING SERVICES &#40;SSRS&#41;でサポートされるデータソース](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。  
  
 <sup>2</sup>[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint モードのが必要です。 詳細については、「sharepoint [2010 および sharepoint 2013&#41;の Reporting Services Sharepoint モードの &#40;インストール](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)」を参照してください。  
  
### <a name="report-server-database-server-edition-requirements"></a>レポート サーバー データベースのサーバー エディション  
 レポート サーバー データベースを作成するときは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のすべてのエディションでデータベースをホストできるわけではないことに注意してください。 次の表に、 [!INCLUDE[ssDE](../includes/ssde-md.md)] の特定のエディションで使用できる [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のエディションを示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services のエディション|データベースをホストするために使用するデータベース エンジン インスタンスのエディション|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Standard Edition、Business Intelligence Enterprise Edition (ローカルまたはリモート)|  
|ビジネス インテリジェンス|Standard Edition、Business Intelligence Enterprise Edition (ローカルまたはリモート)|  
|Standard|Standard Edition、Enterprise Edition (ローカルまたはリモート)|  
|Web|Web Edition (ローカルのみ)|  
|Express with Advanced Services|Express with Advanced Services (ローカルのみ)|  
|評価|評価|  
  
##  <a name="business-intelligence-clients"></a><a name="BIClients"></a>ビジネスインテリジェンスクライアント  
 次のソフトウェア クライアント アプリケーションを Microsoft ダウンロード センターから入手できます。これらのアプリケーションは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで使用するビジネス インテリジェンス ドキュメントの作成に役立ちます。 作成したドキュメントをサーバー環境でホストする場合は、そのドキュメントの種類でサポートされている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエディションを使用してください。 これらのクライアント アプリケーションで作成したドキュメントをホストするのに必要なサーバー機能を備えた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを次の表に示します。  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)]|はい|はい|Yes|||||  
|Excel および Visio 2010 用データ マイニング アドイン|はい|はい|Yes|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010|はい|Yes||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|はい|Yes||||||  
  
> [!NOTE]
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] は Excel アドインで、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には依存しません。 ただし、SharePoint で [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] ワークブックの共有およびコラボレーションを行うには、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] が必要です。この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise および Business Intelligence エディションの一部として使用できます。  
> 2.  上記の表は、これらのクライアント ツールを有効にするために必要な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを示しています。ただし、これらの機能は、どのエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にホストされているデータにもアクセスできます。  
  
##  <a name="spatial-and-location-services"></a><a name="Spatial"></a>空間サービスとロケーションサービス  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|空間インデックス|はい|はい|はい|はい|はい|はい|Yes|  
|平面データ型と測地データ型|はい|はい|はい|はい|はい|はい|Yes|  
|高度な空間的なライブラリ|はい|はい|はい|はい|はい|はい|はい|  
|業界標準の空間データ形式のインポート/エクスポート|はい|はい|はい|はい|はい|はい|Yes|  
  
##  <a name="additional-database-services"></a><a name="Add_DBServices"></a>その他のデータベースサービス  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|はい|はい|はい|はい|はい|はい|Yes|  
|データベース メール|はい|はい|はい|Yes||||  
  
##  <a name="other-components"></a><a name="Other_Components"></a>その他のコンポーネント  
  
|機能名|Enterprise|ビジネス インテリジェンス|Standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|はい|はい||||||  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|StreamInsight Standard Edition||||  
|StreamInsight HA|StreamInsight Premium Edition|||||||  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の製品仕様](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [SQL Server 2014 のインストール](../database-engine/install-windows/installation-for-sql-server.md)   
 [SQL Server 2014 のクイック スタート インストール](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
