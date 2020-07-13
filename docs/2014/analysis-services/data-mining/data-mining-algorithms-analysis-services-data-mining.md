---
title: データマイニングアルゴリズム (Analysis Services-データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- clustering [Data Mining]
- learning algorithms
- data mining [Analysis Services], models
- algorithms [data mining]
- mining models [Analysis Services], algorithms
- inductive learning
- mining models [Analysis Services], creating
- data mining [Analysis Services], algorithms
- machine learning algorithms [Analysis Services]
ms.assetid: ed1fc83b-b98c-437e-bf53-4ff001b92d64
author: minewiskan
ms.author: owend
ms.openlocfilehash: 81d86ba50c76c167e0f6d17cd0dee7e00e6ac938
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84523379"
---
# <a name="data-mining-algorithms-analysis-services---data-mining"></a>データ マイニング アルゴリズム (Analysis Services - データ マイニング)
  *データマイニングアルゴリズム*は、データからデータマイニングモデルを作成する一連のヒューリスティックと計算です。 モデルを作成するために、データ マイニング アルゴリズムは、まず提供されたデータを分析し、特定の種類のパターンまたは傾向を探します。 この分析の結果は、マイニング モデルを作成するための最適化されたパラメーターを定義するために使用されます。 これらのパラメーターはデータセット全体に適用され、実用的なパターンおよび詳細な統計情報が抽出されます。  
  
 アルゴリズムによってデータから作成されるマイニング モデルは、次のようにさまざまな形式を取ります。  
  
-   データセット内のケースの関係を説明するクラスターのセット  
  
-   結果を予測し、基準を変更するとその結果がどのように影響を受けるのかを示すデシジョン ツリー  
  
-   売上を予想する数学的モデル  
  
-   複数の製品を 1 つのトランザクションにグループ化する方法、およびそれらの製品がまとめて購入される確率を示すルールのセット  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、データマイニングソリューションで使用する複数のアルゴリズムが用意されています。 これらのアルゴリズムは、データ マイニングで使用される最も人気のある方法論のうちのいくつかを実装したものです。 どの Microsoft データ マイニング アルゴリズムも、カスタマイズ可能であり、用意されている API または SQL Server Integration Services のデータ マイニング コンポーネントを使用して十分にプログラムできます。  
  
 また、OLE DB for Data Mining 仕様に準拠するサードパーティ製アルゴリズムを使用することも、またはサービスとして登録してから SQL Server データ マイニング フレームワーク内で使用できるカスタム アルゴリズムを開発することもできます。  
  
## <a name="choosing-the-right-algorithm"></a>適切なアルゴリズムの選択  
 特定の分析タスクに使用する最適なアルゴリズムを選択するのが困難な場合があります。 異なるアルゴリズムを使用して同じビジネス タスクを実行できる一方、各アルゴリズムによって異なる結果が生成されたり、一部のアルゴリズムでは複数の種類の結果が生成されたりする場合があります。 たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムは、予測だけでなく、データセット内の列の数を減らす方法としても使用できます。これは、デシジョン ツリーが、最終的なマイニング モデルに影響を与えない列を識別できるためです。  
  
### <a name="choosing-an-algorithm-by-type"></a>種類別アルゴリズムの選択  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、次の種類のアルゴリズムが含まれます。  
  
-   **分類アルゴリズム** 。データセット内の他の属性に基づいて、1 つまたは複数の離散変数を予測します。  
  
-   **回帰アルゴリズム**では、データセット内の他の属性に基づいて、利益や損失などの1つ以上の連続変数を予測します。  
  
-   **分割アルゴリズム** 。データを、類似したプロパティを持つアイテムのグループまたはクラスターに分割します。  
  
-   **アソシエーション アルゴリズム** 。データセット内の異なる属性間の相関関係を検出します。 この種類のアルゴリズムの最も一般的な使用例は、マーケット バスケット分析で使用するアソシエーション ルールの作成です。  
  
-   **シーケンス分析アルゴリズム**は、Web パスフローなど、データ内の頻度の高いシーケンスまたはエピソードを要約します。  
  
 ただし、ソリューションが複数ある中で、1 つのアルゴリズムに限定される必要はありません。 経験豊富なアナリストであれば、ある 1 つのアルゴリズムを使用して最も効果的な入力 (つまり変数) を判断し、次に別のアルゴリズムを適用してそのデータに基づいて特定の結果を予測するものです。 SQL Server データ マイニングでは、1 つのマイニング構造上に複数のモデルを構築できます。そのため、1 つのデータ マイニング ソリューション内でクラスタリング アルゴリズム、デシジョン ツリー モデル、および Naïve Bayes モデルを使用して、データに関するさまざまなビューを得ることができます。 また、1 つのソリューション内で複数のアルゴリズムを使用して、個別のタスクを実行することもできます。たとえば、回帰を使用して財務予測を取得したり、ニューラル ネットワーク アルゴリズムを使用して売上に影響を及ぼす因子を分析したりできます。  
  
### <a name="choosing-an-algorithm-by-task"></a>タスク別アルゴリズムの選択  
 特定のタスクで使用するアルゴリズムの選択の参考として、各アルゴリズムが長年使用されてきたタスクを次の表に示します。  
  
|タスクの例|使用する Microsoft アルゴリズム|  
|-----------------------|---------------------------------|  
|**不連続属性の予測**<br /><br /> 見込み客リスト内の顧客について、見込みがあるかないかをフラグで示します。<br /><br /> あるサーバーに半年以内に障害が発生する確率を計算します。<br /><br /> 患者の転帰を分類し、関連因子を探ります。|[Microsoft デシジョンツリーアルゴリズム](microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム](microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft クラスタリングアルゴリズム](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム](microsoft-neural-network-algorithm.md)|  
|**連続属性の予測**<br /><br /> 翌年の売上を予測します。<br /><br /> 過去の歴史的、季節的傾向を考慮に入れて、来場者を予測します。<br /><br /> 人口統計を考慮に入れて、リスク スコアを生成します。|[Microsoft デシジョンツリーアルゴリズム](microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft Time Series アルゴリズム](microsoft-time-series-algorithm.md)<br /><br /> [Microsoft 線形回帰アルゴリズム](microsoft-linear-regression-algorithm.md)|  
|**シーケンスの予測**<br /><br /> ある企業の Web サイトのクリックストリーム分析を実行します。<br /><br /> サーバーの障害につながる要因を分析します。<br /><br /> 外来患者の来院中の一連の行動を把握し分析して、共通する行動に関するベスト プラクティスを組み立てます。|[Microsoft シーケンス クラスタリング アルゴリズム](microsoft-sequence-clustering-algorithm.md)|  
|**トランザクション内の共通アイテムのグループの検索**<br /><br /> マーケット バスケット分析を使用して、製品の配置を決定します。<br /><br /> ある顧客に追加購入を勧める製品を提案します。<br /><br /> ある 1 件のイベントへの来場者の調査データを分析して、相関関係のある行動またはブースを特定し、今後の活動計画を立てます。|[Microsoft アソシエーション アルゴリズム](microsoft-association-algorithm.md)<br /><br /> [Microsoft デシジョンツリーアルゴリズム](microsoft-decision-trees-algorithm.md)|  
|**類似した項目のグループの検索**<br /><br /> 人口統計や行動などの属性に基づいて、患者リスク プロファイル グループを作成します。<br /><br /> ユーザーを閲覧パターンと購買パターンで分析します。<br /><br /> 同じような使用状況特性を持つサーバーを特定します。|[Microsoft クラスタリングアルゴリズム](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム](microsoft-sequence-clustering-algorithm.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されている各データ マイニング アルゴリズムの学習用リソースのリンクを次の表に示します。  
  
|||  
|-|-|  
|**基本的なアルゴリズムの説明**|アルゴリズムが行うことと機能のしくみについて説明し、そのアルゴリズムが役に立つ可能性のあるビジネス シナリオの概要を説明します。|  
||[Microsoft アソシエーション アルゴリズム](microsoft-association-algorithm.md)<br /><br /> [Microsoft クラスタリングアルゴリズム](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft デシジョンツリーアルゴリズム](microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft 線形回帰アルゴリズム](microsoft-linear-regression-algorithm.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム](microsoft-logistic-regression-algorithm.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム](microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム](microsoft-neural-network-algorithm.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム](microsoft-sequence-clustering-algorithm.md)<br /><br /> [Microsoft Time Series アルゴリズム](microsoft-time-series-algorithm.md)|  
|**テクニカルリファレンス**|アルゴリズムの実装について、必要に応じて学術的参考文献を示しながら、技術的詳細を説明します。 アルゴリズムの動作を制御したり、モデルの結果をカスタマイズしたりするために設定できるパラメーターを列挙します。 データ要件について説明し、可能であればパフォーマンスのヒントを提供します。|  
||[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](microsoft-association-algorithm-technical-reference.md)<br /><br /> [Microsoft クラスタリング アルゴリズム テクニカル リファレンス](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](microsoft-time-series-algorithm-technical-reference.md)|  
|**モデル コンテンツ**|各種類のデータ マイニング モデル内で情報がどのように構造化されるのか、および各ノードに格納された情報を解釈する方法について説明します。|  
||[アソシエーション モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md)<br /><br /> [クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)<br /><br /> [デシジョン ツリー モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)<br /><br /> [線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)<br /><br /> [ロジスティック回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-logistic-regression-models.md)<br /><br /> [Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)<br /><br /> [ニューラル ネットワーク モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)<br /><br /> [シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-sequence-clustering-models.md)<br /><br /> [タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)|  
|**データ マイニング クエリ**|各モデルの種類で使用できる複数のクエリを紹介します。 たとえば、モデル内のパターンをさらに理解できるようにするコンテンツ クエリや、それらのパターンに基づいて予測できるよう支援する予測クエリなどがあります。|  
||[結合モデルのクエリ例](association-model-query-examples.md)<br /><br /> [クラスタリング モデルのクエリ例](clustering-model-query-examples.md)<br /><br /> [デシジョン ツリー モデルのクエリ例](decision-trees-model-query-examples.md)<br /><br /> [線形回帰モデルのクエリ例](linear-regression-model-query-examples.md)<br /><br /> [ロジスティック回帰モデルのクエリ例](logistic-regression-model-query-examples.md)<br /><br /> [Naive Bayes モデルのクエリ例](naive-bayes-model-query-examples.md)<br /><br /> [Neural Network Model Query Examples](neural-network-model-query-examples.md)<br /><br /> [Sequence Clustering Model Query Examples](sequence-clustering-model-query-examples.md)<br /><br /> [Time Series Model Query Examples](time-series-model-query-examples.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|**トピック**|**説明**|  
|---------------|---------------------|  
|あるデータ マイニング モデルで使用されるアルゴリズムを判断します。|[マイニング モデルの作成に使用されたパラメーターのクエリ](query-the-parameters-used-to-create-a-mining-model.md)|  
|カスタム プラグイン アルゴリズムを作成します。|[プラグイン アルゴリズム](plugin-algorithms.md)|  
|アルゴリズム固有のビューアーを使用して、モデルを調査します。|[データ マイニング モデル ビューアー](data-mining-model-viewers.md)|  
|汎用のテーブル フォーマットを使用して、モデルのコンテンツを表示します。|[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)|  
|データをセットアップし、アルゴリズムを使用してモデルを作成する方法について学びます。|[マイニング構造 (Analysis Services - データ マイニング)](mining-structures-analysis-services-data-mining.md)<br /><br /> [マイニング モデル (Analysis Services - データ マイニング)](mining-models-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a>参照  
 [データ マイニング ツール](data-mining-tools.md)  
  
  
