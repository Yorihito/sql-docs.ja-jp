---
title: 'チュートリアル: レポートへの縦棒グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 723e8fe5f657d3b9eda2d6ab73966830a13a3aac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099132"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>チュートリアル: レポートへの縦棒グラフの追加 (レポート ビルダー)
  縦棒グラフでは、カテゴリ別にグループ化された縦棒のセットとして系列が表示されます。 縦棒グラフは次の場合に便利です。  
  
-   時間の経過に伴うデータの変化を示す。  
  
-   複数の系列の相対値を比較する。  
  
-   移動平均を表示して傾向を示す。  
  
 次の図に、これから作成する、移動平均が含まれた縦棒グラフを示します。  
  
 ![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>学習内容  
 このチュートリアルでは、次の方法を学習します。  
  
1.  [グラフ ウィザードからグラフ レポートを作成する](#Chart)  
  
2.  [グラフの種類を選択する](#ChartType)  
  
3.  [横軸の形式とラベルを設定する](#Horizontal)  
  
4.  [凡例を移動する](#Legend)  
  
5.  [グラフのタイトルを設定する](#ChartTitle)  
  
6.  [縦軸の形式とラベルを設定する](#Vertical)  
  
7.  [移動平均を追加する](#Average)  
  
8.  [レポートタイトルを追加する](#Title)  
  
9. [レポートを保存する](#Save)  
  
> [!NOTE]  
>  このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。 レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。  
  
 このチュートリアルの推定所要時間: 15 分  
  
## <a name="requirements"></a>要件  
 要件の詳細については、[「チュートリアルの前提条件 (レポート ビルダー)」](../reporting-services/report-builder-tutorials.md) を参照してください。  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a>1. グラフウィザードからグラフレポートを作成する  
 [**はじめに**] ダイアログボックスで、グラフウィザードを使用して埋め込みデータセットを作成し、共有データソースを選択して、縦棒グラフを作成します。  
  
> [!NOTE]  
>  このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。 このため、クエリが非常に長くなっています。 ビジネス環境でクエリにデータを含めることはありません。 これは、学習に使用することのみを目的としています。  
  
#### <a name="to-create-a-new-chart-report"></a>新しいグラフ レポートを作成するには  
  
1.  **[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。  
  
     [**はじめに**] ダイアログボックスが表示されます。  
  
    > [!NOTE]  
    >  [**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[グラフ ウィザード]** をクリックします。  
  
4.  [**データセットの選択] ページ**で、[**データセットの作成**] をクリックし、[**次へ**] をクリックします。  
  
5.  **[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。 ユーザー名とパスワードの入力が必要な場合があります。  
  
    > [!NOTE]  
    >  適切な権限を持っている限り、選択するデータ ソースは重要ではありません。 データ ソースからはデータを取得しません。 詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。  
  
6.  **[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。  
  
7.  次のクエリをクエリ ペインに貼り付けます。  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。  
  
9. **[次へ]** をクリックします。  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. グラフの種類を選択する  
 あらかじめ定義されているさまざまなグラフの種類から選択できます。  
  
#### <a name="to-add-a-column-chart"></a>縦棒グラフを追加するには  
  
1.  **[グラフの種類の選択]** ページでは、縦棒グラフが既定のグラフの種類です。 **[次へ]** をクリックします。  
  
2.  **[グラフのフィールドの配置]** ページで、SalesDate フィールドを **[カテゴリ]** にドラッグします。 カテゴリは横軸に表示されます。  
  
3.  Sales フィールドを **[値]** にドラッグします。 販売の合計値の総計が 1 日ごとに集計されるので、 **[値]** ボックスには Sum(Sales) が表示されます。 値は縦軸に表示されます。  
  
4.  **[次へ]** をクリックします。  
  
5.  [**スタイルの選択**] ページの [スタイル] ボックスで、スタイルを選択します。  
  
     スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。 スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。  
  
6.  **[完了]** をクリックします。  
  
     グラフがデザイン画面に追加されます。  
  
7.  グラフをクリックして、グラフのハンドルを表示します。 グラフの右下隅をドラッグして、グラフのサイズを大きくします。 レポート デザイン画面も、グラフ サイズに合わせて大きくなります。  
  
8.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a>3. 横軸の書式を設定してラベルを付ける  
 既定では、横軸の値が一般的な形式で表示されます。この場合、グラフのサイズに合わせて自動的にスケーリングされます。  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>横軸に表示される日付の書式を変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  横軸を右クリックし、[**横軸のプロパティ**] をクリックします。  
  
3.  [**数値**] をクリックします。  
  
4.  [**カテゴリ**] で [**日付**] を選択します。  
  
5.  **[型]** ボックスで **[2000 年 1 月 31 日]** を選択します。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [ホーム] タブで **[実行]** をクリックして、レポートをプレビューします。  
  
 選択した日付書式で日付が表示されます。 グラフの横軸を見ると、すべてのカテゴリに対してラベルが表示されているわけではないことがわかります。 既定では、軸の横に収まるラベルだけが表示されます。  
  
 ラベルを回転して間隔を指定することによってラベル表示をカスタマイズできます。  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>軸ラベルを回転して横軸の表示間隔を変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  横軸のタイトルを右クリックし、[軸の**タイトルの表示**] をクリックしてタイトルを削除します。 横軸には日付が表示されるので、タイトルは必要ありません。  
  
3.  横軸を右クリックし、[横軸の**プロパティ**] をクリックします。  
  
4.  [軸の**範囲と間隔**] の下の [**軸のオプション**] ページで、[**間隔**] に「 **3** 」と入力します。 3 日ごとの日付がグラフに表示されるようになります。  
  
5.  [**ラベル**] をクリックします。  
  
6.  [**軸ラベルの自動調整オプションの変更**] で、[**自動調整を無効にする**] を選択します。  
  
7.  **[ラベルの回転角度]** で **[-90]** を選択します。  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     横軸のサンプル テキストが 90 度回転します。  
  
9. **[実行]** をクリックして、レポートをプレビューします。  
  
 グラフでは、ラベルが回転して 3 日ごとに表示されています。  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a>4. 凡例を移動する  
 凡例は、カテゴリと系列データから自動的に作成されます。  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>凡例を縦棒グラフのグラフ領域の下に移動するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフの凡例を右クリックし、[**凡例のプロパティ**] をクリックします。  
  
3.  [**レイアウトと位置**] で、別の位置を選択します。 たとえば、下部中央の位置を選択します。  
  
     凡例をグラフの上または下に配置すると、凡例のレイアウトが縦方向から横方向に変更されます。 **[レイアウト]** ドロップダウン リストから、異なるレイアウトを選択できます。  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (省略可) このチュートリアルではカテゴリが 1 つしかないので、凡例は必要ありません。 凡例を削除するには、凡例を右クリックし、[**凡例の削除**] をクリックします。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a>5. グラフのタイトルをする  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>グラフ領域の上に表示されるグラフのタイトルを変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフの上部にある [**グラフのタイトル**] というテキストを選択し、「**店舗販売注文合計**」と入力します。  
  
3.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a>6. 縦軸の形式とラベルを設定する  
 既定では、縦軸の値が一般的な形式で表示されます。この場合、グラフのサイズに合わせて自動的にスケーリングされます。  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>縦軸に表示される数値を通貨形式に変更するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフの側面に沿った垂直軸のラベルをダブルクリックして選択します。  
  
3.  リボンの [**ホーム**] タブの [**数値**] グループで、[**通貨**] ボタンをクリックします。 軸ラベルの表示が、通貨形式に変更されます。  
  
4.  リボンの [**ホーム**] タブの [**数値**] グループで、[**小数点表示桁下げ**] ボタンを2回クリックして、最も近いドルに丸めた数値を表示します。  
  
5.  縦軸を右クリックし、[**縦軸のプロパティ**] をクリックします。  
  
6.  [**数値**] をクリックします。 [**カテゴリ**] ボックスでは [**通貨**] が既に選択されており、[**小数点以下**桁数] は既に**0** (ゼロ) になっています。  
  
7.  [**値の表示**方法] ボックスで、[**千**] をクリックします。  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. グラフの側面に沿った縦軸のタイトルを右クリックし、[**軸のタイトルのプロパティ**] をクリックします。  
  
10. [**タイトルのテキスト**] フィールドのテキストを「 **Sales Total (1000 単位)**」というテキストに置き換えます。 タイトルの表示形式に関連した各種オプションを指定することもできます。  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a>7. 移動平均を追加する  
  
#### <a name="to-add-a-moving-average"></a>移動平均を追加するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  グラフをダブルクリックして、 **グラフ データ** ペインを表示します。  
  
3.  [**値**] 領域にある **[Sum (Sales)]** フィールドを右クリックし、[**計算系列の追加**] をクリックします。  
  
4.  **[数式]** で、 **[移動平均]** が選択されていることを確認します。  
  
5.  **[数式パラメーターの設定]** の **[期間]** で、 **[4]** を選択します。  
  
6.  [**罫線**] をクリックします。  
  
7.  [**線の幅**] で [ **1pt から 3pt**] を選択します。  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. **[実行]** をクリックして、レポートをプレビューします。  
  
 グラフに、4 日ごとに平均値を求めた日付別の売上合計の移動平均を示す線が表示されます。  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a>8. レポートタイトルを追加する  
  
#### <a name="to-add-a-report-title"></a>レポート タイトルを追加するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。  
  
3.  「 **Sales Chart**」と入力し、enter キーを押し、次のように**2009**入力します。  
  
     **Sales Chart**  
  
     **January to December 2009**  
  
4.  [ **Sales Chart**] を選択し、リボンの [**ホーム**] タブの [**フォント**] セクションで [**太字**] ボタンをクリックします。  
  
5.  **1 月から12月 2009**を選択し、[**ホーム**] タブの [**フォント**] セクションで、フォントサイズを**10**に設定します。  
  
6.  Optional下部の端をクリックしたときに双方向矢印を下に引いて、2行のテキストに合わせて**タイトル**のテキストボックスの高さを大きくする必要がある場合があります。  
  
     このタイトルは、レポートの最上部に表示されます。 ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。  
  
7.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="9-save-the-report"></a><a name="Save"></a>9. レポートを保存する  
  
#### <a name="to-save-the-report"></a>レポートを保存するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  レポート ビルダー のボタンの **[名前を付けて保存]** をクリックします。  
  
3.  **[名前]** に「 **Sales Order Column Chart**」と入力します。  
  
4.  **[Save]** (保存) をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 これで、「レポートへの縦棒グラフの追加」チュートリアルを終了します。 グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md)   
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  
