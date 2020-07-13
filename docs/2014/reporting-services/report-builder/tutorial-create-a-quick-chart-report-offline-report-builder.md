---
title: チュートリアル:オフラインでのクイック グラフ レポートの作成 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5cd666ec589737d83717e9b435a260bd2a0d0ef6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176897"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a>チュートリアル: オフラインでのクイック グラフ レポートの作成 (レポート ビルダー)
  このチュートリアルでは、ウィザードを使用して円グラフを作成し、少し変更して実行可能な操作を確認します。 このチュートリアルは 2 つの異なる方法で実行できます。 どちらの方法でも、次の図に示すような円グラフが同じ結果になります。

 ![実行ビューの "My First Pie Chart"](../media/rs-my1stpierunview.gif "実行ビューの最初の円グラフ")

## <a name="prerequisites"></a>前提条件
 XML データを使用するか [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用するかにかかわらず、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] レポート ビルダーにアクセスできることが必要です。 スタンドアロン バージョン、またはレポート マネージャーや SharePoint サイトから利用できる ClickOnce バージョンを実行できます。 ClickOnce バージョンでは、最初の手順であるレポートビルダーを開く方法のみが異なります。 詳細については、「 [Install、Uninstall、およびレポートビルダー Support](../install-uninstall-and-report-builder-support.md)」を参照してください。

##  <a name="two-ways-to-do-this-tutorial"></a><a name="TwoWays"></a>このチュートリアルを実行する2つの方法

-   [XML データを使用して円グラフを作成する](#CreatePieChartXML)

-   [データを含む SQL クエリを使用して円グラフを作成する](#CreatePieQueryData)

### <a name="using-xml-data-for-this-tutorial"></a>このチュートリアルでの XML データの使用
 このトピックからコピーしてウィザードに貼り付けた XML データを使用できます。 レポート サーバーまたは SharePoint 統合モードのレポート サーバーに接続している必要はありません。[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスへのアクセスも不要です。

 [XML データを使用して円グラフを作成する](#CreatePieChartXML)

### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a>このチュートリアル用のデータを含む Transact-SQL クエリの使用
 データを含むクエリをこのトピックからコピーし、ウィザードに貼り付けることができます。 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスの名前と、任意のデータベースに読み取り専用でアクセスするのに十分な資格情報が必要です。 チュートリアルのデータセット クエリでは、リテラル データを使用します。ただし、クエリは、レポート データセットに必要なメタデータを返すように、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスで処理される必要があります。

 [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用する利点は、レポート ビルダーの他のすべてのチュートリアルで同じ方法が使用されているため、他のチュートリアルを実行するときに既に手順がわかっていることです。

 [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリの場合、他にもいくつか必要な前提条件があります。 詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../report-builder-tutorials.md)」を参照してください。

 [データを含む SQL クエリを使用して円グラフを作成する](#CreatePieQueryData)

## <a name="also-in-this-article"></a>この記事の他の内容
 [ウィザードの実行後](#AfterWizard)

 [次の内容](#WhatsNext)

##  <a name="creating-the-pie-chart-with-xml-data"></a><a name="CreatePieChartXML"></a>XML データを使用して円グラフを作成する

#### <a name="to-create-the-pie-chart-with-xml-data"></a>XML データを使用して円グラフを作成するには

1.  **[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。

     [**はじめに**] ダイアログボックスが表示されます。

    > [!NOTE]
    >  [**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。

2.  左側のウィンドウで、[**レポート**] が選択されていることを確認します。

3.  右ペインで、 **[グラフ ウィザード]** をクリックし、 **[作成]** をクリックします。

4.  **[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。

5.  **[データ ソースへの接続の選択]** ページで **[新規作成]** をクリックします。

     **[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。

6.  データ ソースに任意の名前を付けることができます。 **[名前]** ボックスに、「 **MyPieChart**」と入力します。

7.  [**接続の種類の選択**] ボックスで、[XML] をクリックし**ます。**

8.  [**資格情報**] タブで、[現在の Windows ユーザーを使用する] を選択し**ます。Kerberos 委任が必要な場合**は、[ **OK]** をクリックします。

9. **[データ ソースへの接続の選択]** ページで **[MyPieChart]** をクリックし、 **[次へ]** をクリックします。

10. 次のテキストをコピーし、[**クエリのデザイン**] ページの中央にある大きいボックスに貼り付けます。

    ```
    <Query>
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>
    <XmlData>
    <Root>
    <S Sales="150">
      <C FullName="Jae Pak" />
    </S>
    <S Sales="350">
      <C FullName="Jillian  Carson" />
    </S>
    <S Sales="250">
      <C FullName="Linda C Mitchell" />
    </S>
    <S Sales="500">
      <C FullName="Michael Blythe" />
    </S>
    <S Sales="450">
      <C FullName="Ranjit Varkey" />
    </S>
    </Root>
    </XmlData>
    </Query>
    ```

11. (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。

12. **[次へ]** をクリックします。

13. **[グラフの種類の選択]** ページで **[円]** をクリックし、 **[次へ]** をクリックします。

14. **[グラフのフィールドの配置]** ページの **[使用できるフィールド]** ボックスで、**[Sales]** フィールドをダブルクリックします。

     このフィールドは数値なので、 **[値]** ボックスに自動的に移動します。

15. **[FullName]** フィールドを **[使用できるフィールド]** ボックスから **[カテゴリ]** ボックスにドラッグし (または、ダブルクリックすると **[カテゴリ]** ボックスに移動します)、**[次へ]** をクリックします。

16. [**スタイルの選択**] ページでは、既定で [**海上**] が選択されています。 他のスタイルをクリックして、その違いを確認します。

17. **[完了]** をクリックします。

     デザイン画面に、新しい円グラフ レポートが表示されます。 表示内容は見本です。 凡例には販売員の名前ではなく Full Name 1、Full Name 2 などが示されており、円のスライスのサイズは正確ではありません。 これは、レポートがどのように表示されるか概要を見るためだけのものです。

18. 実際の円グラフを表示するには、リボンの **[ホーム]** タブで **[実行]** をクリックします。

 トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")

##  <a name="creating-the-pie-chart-with-a-tsql-query"></a><a name="CreatePieQueryData"></a>[!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用して円グラフを作成する

#### <a name="to-create-the-pie-chart-with-a-tsql-query-that-contains-data"></a>データを含む [!INCLUDE[tsql](../../../includes/tsql-md.md)] クエリを使用して円グラフを作成するには

1.  **[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。

2.  [**新しいレポートまたはデータセット**] ダイアログボックスで、左側のペインで [**レポート**] が選択されていることを確認します。

3.  右ペインで、 **[グラフ ウィザード]** をクリックし、 **[作成]** をクリックします。

4.  **[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。

5.  **[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。 ユーザー名とパスワードの入力が必要な場合があります。

    > [!NOTE]
    >  適切な権限を持っている限り、選択するデータ ソースは重要ではありません。 データ ソースからはデータを取得しません。 詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../report-builder-tutorials.md)」を参照してください。

6.  [**クエリのデザイン**] ページで、[**テキストとして編集**] をクリックします。

7.  次のクエリをクエリ ペインに貼り付けます。

    ```
    SELECT 150 AS Sales, 'Jae Pak' AS FullName 
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName 
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName 
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName 
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName 
    ```

8.  (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。

9. **[次へ]** をクリックします。

10. **[グラフの種類の選択]** ページで **[円]** をクリックし、 **[次へ]** をクリックします。

11. **[グラフのフィールドの配置]** ページの **[使用できるフィールド]** ボックスで、**[Sales]** フィールドをダブルクリックします。

     このフィールドは数値なので、 **[値]** ボックスに自動的に移動します。

12. **[FullName]** フィールドを **[使用できるフィールド]** ボックスから **[カテゴリ]** ボックスにドラッグし (または、ダブルクリックすると **[カテゴリ]** ボックスに移動します)、**[次へ]** をクリックします。

13. **[スタイルの選択]** ページでは、既定で [オーシャン] が選択されています。 他のスタイルをクリックして、その違いを確認します。

14. **[完了]** をクリックします。

     デザイン画面に、新しい円グラフ レポートが表示されます。 表示内容は見本です。 凡例には販売員の名前ではなく Full Name 1、Full Name 2 などが示されており、円のスライスのサイズは正確ではありません。 これは、レポートがどのように表示されるか概要を見るためだけのものです。

15. 実際の円グラフを表示するには、リボンの **[ホーム]** タブで **[実行]** をクリックします。

 トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")

##  <a name="after-you-run-the-wizard"></a><a name="AfterWizard"></a>ウィザードを実行した後
 円グラフ レポートが完成したので、操作してみます。 変更を続行するには、リボンの **[実行]** タブで **[デザイン]** をクリックします。

### <a name="make-the-chart-bigger"></a>グラフの拡大
 円グラフを拡大するには、 グラフ内の要素ではなくグラフをクリックして選択し、右下隅をドラッグしてサイズを変更します。

### <a name="add-a-report-title"></a>レポート タイトルの追加
 グラフ上部の **[グラフのタイトル]** というテキストを選択し、「 **Sales Pie Chart**」などのタイトルを入力します。

### <a name="add-percentages"></a>パーセンテージの追加

##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>円グラフにパーセンテージをラベルとして表示するには

1.  円グラフを右クリックし、[**データラベルの表示**] を選択します。 円グラフの各スライス内にデータ ラベルが表示されます。

2.  ラベルを右クリックし、[**系列ラベルのプロパティ**] を選択します。 **[系列ラベルのプロパティ]** ダイアログ ボックスが表示されます。

3.  [ `#PERCENT{P0}` **ラベルデータ**] オプションに「」と入力します。

     `{P0}` を指定すると、小数点以下を含まないパーセンテージが表示されます。 「`#PERCENT`」とだけ入力すると、小数点以下 2 桁を含む数値になります。 `#PERCENT` は計算または関数を実行するキーワードで、他にも多数あります。

 グラフのラベルと凡例をカスタマイズする方法の詳細については、「[円グラフへのパーセンテージの表示 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)」および「[凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md)」を参照してください。

 トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")

##  <a name="whats-next"></a><a name="WhatsNext"></a>次は何ですか?
 レポート ビルダーでレポートを初めて自分で作成したので、他のチュートリアルに取り組んで独自のデータからレポートを作成する準備ができました。 レポートビルダーを実行するには、実際にデータソースに接続する*接続文字列*を使用して、データベースなどのデータソースにアクセスする権限が必要です。 システム管理者がこの情報を保持し、ユーザーを設定できます。

 他のチュートリアルを実行するには、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスの名前と、任意のデータベースに読み取り専用でアクセスするのに十分な資格情報が必要です。 これもシステム管理者が設定できます。

 最後に、レポートをレポート サーバーまたはレポート サーバーと統合されている SharePoint サイトに保存するには、URL と権限が必要です。 作成したレポートは自分のコンピューターから直接実行できますが、レポート サーバーまたは SharePoint サイトから実行するとレポートの機能が増えます。 自分のレポートまたはその他のレポートをパブリッシュ元のレポート サーバーまたは SharePoint サイトから実行する権限が必要です。 アクセス権を取得するには、システム管理者に問い合わせてください。

 開始する前に、いくつかの概念や用語について確認しておくと役立つ場合があります。 詳細については、「[レポート作成の概念 &#40;レポートビルダーと SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)」を参照してください。 また、レポートを初めて自分で作成する前に、計画の時間を取ってください。 時間を費やす価値があります。 詳細については、「 [Planning a Report &#40;レポートビルダー&#41;](../report-design/planning-a-report-report-builder.md)」を参照してください。

 トップ[に](#TwoWays)戻る![リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")

## <a name="see-also"></a>参照
 [チュートリアル &#40;](../report-builder-tutorials.md) [SQL Server 2014 でのレポートビルダー](report-builder-in-sql-server-2016.md)&#41;レポートビルダー


