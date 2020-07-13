---
title: Excel 用のデータマイニングクライアント (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Data Mining Client
- wizards
- getting started
ms.assetid: e075e2de-11cc-4f71-9603-0b161bca8a24
author: minewiskan
ms.author: owend
ms.openlocfilehash: f41ffd3091ccf38498f1484d9a1bf5a908e50e39
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525940"
---
# <a name="data-mining-client-for-excel-sql-server-data-mining-add-ins"></a>Excel 用のデータ マイニング クライアント (SQL Server データ マイニング アドイン)
  Excel 用データ マイニング クライアントは、データ クレンジング、モデル構築、予測クエリなど共通のデータ マイニング タスクを実行できる一連のツールです。 Excel テーブルまたは範囲のデータを使用することも、外部データ ソースにアクセスすることもできます。  
  
 ![DM](media/dm-tabletools.gif "DM")  
  
-   [データの操作](#bkmk_Data)  
  
     Excel へのデータの読み込み、データのクレンジング、外れ値のチェック、統計サマリーの作成を行います。 また、さまざまな種類のサンプリング、データのプロファイル、外部データを使用したモデルのテストも実行できます。 データ マイニング クライアントは、分析するデータを複雑なスクリプトや ETL プロセスなしで準備する最も簡単な方法です。  
  
-   [モデルの構築と分析](#bkmk_Model)  
  
     これらのツールが提供するウィザード インターフェイスから、クラスタリング (K-Means および EM)、アソシエーション分析、時系列分析、デシジョン ツリーなど、広く普及した実証済みのデータ マイニング アルゴリズムを利用できます。 各ウィザードの詳細モデリング オプションでは、Naïve Bayes やニュートラル ネットワークなど、異なるアルゴリズムを選択することができ、クラスター シードや初期サンプリング サイズなどの動作をカスタマイズできます。  
  
     すべてのデータ マイニング アルゴリズムは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスにホストされ、より複雑なモデルを構築できます。  
  
-   [モデルのテスト、クエリ、および検証](#bkmk_Validate)  
  
     データ マイニング クライアントには、リフト チャートやクロス検証も含めて、モデルをテストする業界標準のツールが用意されています。 用意されているウィザードを使用すると、データセットの有効性と精度を容易にテストできます。 クエリ ウィザードでは、予測およびスコアリングのためにモデルを使用するクエリを作成します。  
  
-   [モデルの表示](#bkmk_ViewModels)  
  
     ほとんどのツールが生成するチャートは Excel に直接保存できます。 モデルを確認するには、[ [Excel でのモデルの参照 &#40;SQL Server データマイニングアドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)ツール] を使用します。  
  
-   [管理、ドキュメント化、配置](#bkmk_UsageMgmt)  
  
     Excel 用のデータ マイニング クライアントではサーバーへのアクティブな接続が維持されるので、作成したデータ マイニング モデルをサーバーに保存して以降のテストで使用できます。または、モデルを実稼働サーバーに保存するとスケーラビリティはさらに高くなります。  
  
##  <a name="work-with-data"></a><a name="bkmk_Data"></a>データの操作  
 データ**準備**グループには、データマイニングタスクの準備としてデータを確認し、クリーンアップするための次のウィザードが含まれています。 また、ほとんどのウィザードでデータをトレーニング セットとテスト セットに分けることができます。  
  
 [データ &#40;SQL Server データマイニングアドインの探索&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 このアドインでは、モデルの構築と格納用に次のデータ接続をサポートしています。  
  
-   モデルの格納および処理用の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーへの接続  
  
-   外部データ ソースへの接続 (オプション)。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースとして定義されるあらゆる種類のデータを使用してモデルを構築できます。または、Excel の既存データを使用することも可能です。  
  
 [データ &#40;SQL Server データマイニングアドインの探索&#41;](explore-data-sql-server-data-mining-add-ins.md)  
 **データの探索**ウィザードを使用すると、選択した列の分布と値を一度にグラフ化することで、データテーブル内のデータの種類と量を理解できます。  
  
 [データマイニングアドイン SQL Server &#40;サンプルデータ&#41;](sample-data-sql-server-data-mining-add-ins.md)  
 モデルのトレーニングとテストのために適切なデータを作成する作業は、データ マイニングの重要な部分ですが、適切なツールがないと面倒になりがちです。 **サンプルデータ**ウィザードを使用すると、モデルに使用されるデータを2つのグループに分割することができます。1つはモデルの作成用で、もう1つはテスト用です。 ランダム サンプリングまたはオーバーサンプリングを使用できます。  
  
 [予測計算 &#40;Excel 用のテーブル分析ツール&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 外れ値の**削除**ウィザードには、外れ値を特定して適切に処理するためのツールがいくつか用意されています。 このウィザードでは、値の分布や外れ値とその他のデータのリレーションシップを表示して、外れ値の削除または変更を判断できます。  
  
 [予測計算 &#40;Excel 用のテーブル分析ツール&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 ラベルの変更ウィザードを使用する**と、分析**の結果をわかりやすくするために、データの新しいラベルを作成できます。 たとえば、データの範囲の名前をよりわかりやすい名前に変更したり、一覧から代表値を選択したりすることができます。  
  
##  <a name="build-models-and-analyze"></a><a name="bkmk_Model"></a>モデルの構築と分析  
 ツールバーの [**データモデリング**] セクションのオプションを使用すると、データからパターンを派生させることができます。属性に基づいてデータの行をグループ化するか、関連付けを探索します。 このツール リボンのウィザードは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で利用できる強力なデータ マイニング アルゴリズムに基づいています。 Excel 用のテーブル分析ツールの類似ツールと異なり、これらのウィザードでは、アルゴリズムの動作をカスタマイズしたり、さまざまなデータ ソースを使用したりできます。  
  
 [分類ウィザード &#40;Excel 用データマイニングアドイン&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
 **分類**ウィザードを使用すると、excel テーブル、excel 範囲、または外部データソースの既存のデータに基づいて分類モデルを作成できます。 分類モデルはデータから共通のパターンを抽出します。そのため、分類モデルを使用すると、グループ化された値に基づいて予測を行うことができます。 たとえば、分類モデルを使用して、収入パターンまたは支出パターンに基づくリスクを予測できます。  
  
 **分類**ウィザードでは、デシジョンツリーアルゴリズム、ロジスティック回帰、単純 Bayes、ニューラルネットワークの各 Microsoft データマイニングアルゴリズムの使用をサポートしています。  
  
 [推定ウィザード &#40;Excel 用データマイニングアドイン&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
 **推定**ウィザードを使用すると、推定モデルを作成できます。 推定モデルは、データからパターンを抽出し、そのパターンを基に、通貨、売上高、日付、時刻など数値による結果を予測します。  
  
 **推定**ウィザードでは、次の Microsoft データマイニングアルゴリズム (デシジョンツリー、線形回帰、ロジスティック回帰、ニューラルネットワーク) が使用されます。  
  
 [Excel 用のテーブル分析ツール &#40;主要な影響元の分析&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 クラスター ウィザードでは、クラスター モデルを構築できます。 クラスター モデルにより、似た特性を共有する行グループが検出されます。 このウィザードは、あらゆる種類のデータのパターンを調べる場合に有用です。  
  
 **クラスター**ウィザードでは、K の意味と EM の両方を含む Microsoft クラスタリングアルゴリズムが使用されます。  
  
 [関連付けウィザード &#40;Excel 用データマイニングクライアント&#41;](associate-wizard-data-mining-client-for-excel.md)  
 **関連付け**ウィザードでは、頻繁に発生するアイテムまたはイベントを検出する Microsoft アソシエーションルールアルゴリズムを使用してデータマイニングモデルを作成できます。 このようなアソシエーション モデルは、特定のアイテムを推薦する場合などに特に有用です。  
  
 **関連付け**ウィザードでは、Microsoft アソシエーションルールアルゴリズムが使用されます。  
  
 [予測ウィザード &#40;Excel 用データマイニングアドイン&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
 **予測**ウィザードでは、時系列の値を予測することができます。 通常、予測で使用されるデータには日付スタンプやシーケンス ID など、ある種の時系列が含まれます。この時系列を使用して抽出したパターンを使用して将来値を予測します。  
  
 **予測**ウィザードでは、Microsoft タイムシリーズアルゴリズムが使用されます。  
  
 [高度なモデリング &#40;Excel 用データマイニングアドイン&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
 データ マイニングの概念を既に理解している場合は、 **高度な**データモデリングオプションを使用すると、他のツールやウィザードに含まれていないカスタマイズを使用して、カスタムデータ構造を作成し、モデルを構築することができます。  
  
##  <a name="test-query-and-validate-models"></a><a name="bkmk_Validate"></a>モデルのテスト、クエリ、および検証  
 [**精度と検証**] ツールバーのウィザードを使用すると、業界標準のテストを使用してモデルの精度を検証したり、モデルを作成するためのデータセットの有効性を評価したりできます。  
  
 [Excel 用のテーブル分析ツール &#40;主要な影響元の分析&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 リフト チャートまたは散布図を生成することにより、データ マイニング モデルのパフォーマンスを評価します。  
  
 [分類マトリックス &#40;SQL Server データマイニングアドイン&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
 モデルによって生成される正確な予測と不正確な予測の概要グラフを作成することにより、分類モデルのパフォーマンスを評価できます。  
  
 [利益チャート &#40;SQL Server データマイニングアドイン&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
 予測に基づいてアクションを実行した場合のコストと利点を含め、予測の精度をグラフ化することにより、データ マイニング モデルの影響について理解できます。  
  
 [相互検証 &#40;SQL Server データマイニングアドイン&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
 データセットの多数のサブセットにわたってモデルの正確性を要約したレポートを作成することにより、モデルの安定度を判断できます。  
  
 また、サーバーに格納されているマイニング モデルに対する予測クエリの入力として、Excel テーブルのデータを使用することもできます。  
  
 [クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)  
 **クエリ**ウィザードを使用すると、既存のデータマイニングモデルに対して予測を作成できます。  
  
 [詳細データ マイニング クエリ エディター](advanced-data-mining-query-editor.md)  
 このツールは、上級ユーザー向けに DMX へのドラッグ アンド ドロップ インターフェイスを提供します。 予測クエリまたは新しいモデルを簡単に作成でき、構文について心配する必要はありません。  
  
##  <a name="view-models"></a><a name="bkmk_ViewModels"></a>モデルの表示  
 作成するモデルは参照用に自動的に開きます。 ただし、サーバー上でモデルを参照して、新しい視覚エフェクトを生成することもできます。 [Visio 図形](viewing-data-mining-models-in-visio-data-mining-add-ins.md)を使用して、モデル図をカスタマイズ可能なキャンバスにエクスポートします。  
  
 [Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
 モデルの各種類に合わせてカスタマイズされた対話型のグラフを使用して、作成したモデルを表示します。  
  
 [Excel 用データマイニングアドイン &#40;マイニングモデルのドキュメント化&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)  
 このウィザードでは、データ セットとモデルのメタデータに関する統計サマリーを提供するレポートが作成されます。このレポートを調査と解釈に役立てることができます。  
  
##  <a name="manage-document-and-deploy"></a><a name="bkmk_UsageMgmt"></a>管理、ドキュメント、展開  
 これらのツールを使用することで、データ マイニング サーバーに接続し、モデルを管理およびエクスポートして、データ マイニング アクティビティを監視できます。  
  
 [データマイニングアドイン SQL Server &#40;モデルの管理&#41;](manage-models-sql-server-data-mining-add-ins.md)  
 必要な権限を持っている場合は、Excel を離れることなく、変更、名前の変更、既存のマイニングモデルおよび構造の処理を削除できます。  
  
 [Excel 用のデータマイニングクライアントのトレース &#40;&#41;](trace-data-mining-client-for-excel.md)  
 [**トレース**] をクリックすると、Excel クライアントとサーバー間の相互作用の継続的なキャプチャが表示され [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。 アクティビティはすべて DMX または XMLA ステートメントとして格納されるため、データ マイニング セッションのトラブルシューティングを行ったり、後で使用するために情報を保存したりできます。  
  
 [データ マイニング サーバーへの接続](connect-to-a-data-mining-server.md)  
 データ マイニングのクライアントとして Excel を使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続を確立する必要があります。 この接続を確立すると、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エンジンにアクセスできます。 また、適切な権限を持っている場合は、この接続により、発見したパターンの格納や、既存のデータ マイニング オブジェクトの変更を行うこともできます。  
  
 [**接続**] ツールバーには、のインスタンスへの接続を管理するためのウィザードが用意されて [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] います。 データ マイニング ツールおよびアルゴリズムを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続を定義する必要があります。 アドインをインストールするときに接続を作成できます。後で接続を追加することもできます。  
  
 **作業の開始**  
 [**はじめに**] ボタンをクリックして構成ウィザードを起動します。このウィザードでは、のインスタンスへの接続を作成 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] し、データマイニングに必要な権限を取得します。  
  
 **ヘルプ**  
 [**ヘルプ**] ドロップダウンメニューには、セットアップを完了してデータマイニングを開始するのに役立つオンラインヘルプ、Web サイト、および構成ウィザードへのリンクが用意されています。  
  
 ヘルプ ページには、アドインのヘルプ、追加のビデオ、デモ、サンプルなどのオンライン リソースへのリンクも記載されています。  
  
## <a name="see-also"></a>参照  
 [Excel 用のテーブル分析ツール](table-analysis-tools-for-excel.md)   
 [データマイニングアドインの &#40;SQL Server Visio データマイニングダイアグラムのトラブルシューティング&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
