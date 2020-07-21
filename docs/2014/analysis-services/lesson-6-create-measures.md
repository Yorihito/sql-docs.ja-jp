---
title: 'レッスン 7: メジャーを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: ef487927098e63c7fc870aa65e55f57faa26767d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542564"
---
# <a name="lesson-7-create-measures"></a>レッスン 7: メジャーを作成する
  このレッスンでは、モデルに含められるメジャーを作成します。 前のレッスンで作成した計算列と同様、メジャーは、基本的には、DAX 数式を使用して作成される計算です。 ただし、計算列とは違い、メジャーはユーザーが選択した " *フィルター*" に基づいて評価されます (たとえば、PivotTable 内の行ラベル フィールドに追加された特定の列やスライサーなど)。   フィルター内の各セルの値は､適用されたメジャーによって求められます｡ メジャーは強力で柔軟な計算なので、ほとんどすべてのテーブル モデルに含めて、数値データに対する動的な計算を実行できます。 詳細については、「[メジャー (SSAS テーブル)](tabular-models/measures-ssas-tabular.md)」を参照してください。  
  
 メジャーを作成するには、メジャー グリッドを使用します。 既定では、各テーブルに空のメジャー グリッドがあります。ただし、通常はすべてのテーブルにメジャーを作成することはありません。 メジャー グリッドは、モデル デザイナーのデータ ビューで、テーブルの下に表示されます。 テーブルのメジャー グリッドを非表示または表示するには､**[テーブル]** メニューをクリックし､**[Show Measure Grid]** をクリックします｡  
  
 メジャーを作成するには、メジャー グリッド内で空のセルをクリックし、数式バーに DAX 数式を入力します。 Enter キーを押して式の入力を完了すると、そのセルにメジャーが表示されます。 またメジャーは､標準の集計関数を使用して作成することもできます｡このためには､列をクリックし､ツールバー上の [AutoSum] ボタン (**∑**) をクリックします｡ オート SUM 機能を使用して作成したメジャーは、その列のすぐ下のメジャー グリッド セルに表示されますが、必要に応じて移動できます。  
  
 このレッスンでは、数式バーに DAX 数式を入力する方法と、オート SUM 機能を使用する方法の両方でメジャーを作成します。  
  
 このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「 [レッスン 6: 計算列の作成](lesson-5-create-calculated-columns.md)」を完了している必要があります。  
  
## <a name="create-measures"></a>メジャーを作成する  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a>Date テーブル内に Days Current Quarter to Date メジャーを作成するには  
  
1.  モデルデザイナーで、 **Date**テーブルをクリックします。  
  
2.  テーブルの下に空のメジャー グリッドが表示されていない場合は、 **[テーブル]** メニューをクリックし、 **[メジャー グリッドの表示]** をクリックします。  
  
3.  メジャー グリッドの左上の空のセルをクリックします｡  
  
4.  テーブルの上の数式バーに次の式を入力します｡  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
     左上のセルにメジャー名 ( **measure 1**) が含まれ、その後に結果**30**が表示されていることに注意してください。 メジャー名は、数式バーの数式の前にも表示されます。  
  
5.  メジャーの名前を変更するには、数式バーで名前 ( **measure 1**) を強調表示し、「」と入力して `Days Current Quarter to Date` 、enter キーを押します。  
  
    > [!TIP]  
    >  数式バーで数式を入力する際には、最初にメジャー名を入力し、続けてコロン (:)、スペース、数式の順に入力することもできます。 この方法を使用すれば、メジャー名を変更する必要はありません。  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a>Date テーブル内に Days in Current Quarter メジャーを作成するには  
  
1.  モデル デザイナー内の **Date** テーブルをアクティブな状態にしたまま、メジャー グリッドで、先ほど作成したメジャーの下の空のセルをクリックします。  
  
2.  数式バーに次の式を入力します｡  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     この式では、最初にメジャー名を入力し、続けてコロン (:) を入力します。  
  
     数式の入力が終了したら、Enter キーを押します。  
  
 未完了の期間と前の期間との間に比較率を作成する場合、数式では、経過した期間の比率を考慮に入れて、それを前の期間内の同じ比率と比較する必要があります。 この場合は、[Days Current Quarter to Date]/[Days in Current Quarter] とすることで、現行期間内の経過比率を割り出すことができます。  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a>Internet Sales テーブル内に Internet Distinct Count Sales Order メジャーを作成するには  
  
1.  モデル デザイナーで、[ **Internet Sales** ] テーブル (タブ) をクリックします。  
  
     テーブルの下にメジャー グリッドが表示されていない場合は、 **[Internet Sales]** テーブル (タブ) を右クリックし、 **[メジャー グリッドの表示]** をクリックします。  
  
2.  **[Sales Order Number]** 列見出しをクリックします。  
  
3.  ツールバーで 「AutoSum」\ (**∑**) ボタンの下向き矢印をクリックし､**DistinctCount** を選択します｡  
  
     AutoSum 機能により､DistinctCount 標準集計式を使用して選択された列のメジャーが自動的に作成されます｡  
  
     メジャー グリッド内の対象列のすぐ下のセルに、メジャー名 ( **Distinct Count Sales Order Number**) が表示されます。 オート SUM 機能を使用して作成したメジャーは、メジャー グリッド内で、関連付けられた列のすぐ下のセルに自動的に配置されます。  
  
4.  メジャー グリッドで新しいメジャーをクリックし、 **[プロパティ]** ウィンドウの **[メジャー名]** に「 **Internet Distinct Count Sales Order**」と入力して名前を変更します。  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a>Internet Sales テーブル内に追加のメジャーを作成するには  
  
1.  AutoSum 機能を使用して次のメジャーを作成し､名前を指定します｡  
  
    |[メジャー名]|Column|オート SUM (∑)|Formula|  
    |------------------|------------|-------------------|-------------|  
    |Internet Order Lines Count|Sales Order Line Number|Count|=COUNT([Sales Order Line Number])|  
    |Internet Total Units|Order Quantity|SUM|=SUM([Order Quantity])|  
    |Internet Total Discount Amount|Discount Amount|SUM|=SUM([Discount Amount])|  
    |Internet Total Product Cost|Total Product Cost|SUM|=SUM([Total Product Cost])|  
    |Internet Total Sales|Sales Amount|SUM|=SUM([Sales Amount])|  
    |Internet Total Margin|Margin|SUM|=SUM([Margin])|  
    |Internet Total Tax Amt|Tax Amt|SUM|=SUM([Tax Amt])|  
    |Internet Total Freight|運送料|SUM|=SUM([Freight])|  
  
2.  メジャー グリッド内で空のセルをクリックし、数式バーを使用して、次の名前のメジャーを作成します。  
  
    > [!IMPORTANT]  
    >  メジャーは次の順序のとおりに作成する必要があります (先行するメジャーは後続のメジャー内の数式から参照されるため)。  
  
    |[メジャー名]|Formula|  
    |------------------|-------------|  
    |Internet Previous Quarter Margin|=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Margin|=TOTALQTD([Internet Total Margin],'Date'[Date])|  
    |Internet Previous Quarter Margin Proportion to QTD|=[Internet Previous Quarter Margin]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
    |Internet Previous Quarter Sales|=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Sales|=TOTALQTD([Internet Total Sales],'Date'[Date])|  
    |Internet Previous Quarter Sales Proportion to QTD|=[Internet Previous Quarter Sales]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
  
 Internet Sales テーブル用に作成されたメジャーは、ユーザー選択のフィルターによって定義された項目に関する重要な財務データ (売上、コスト、利益率など) を分析するためにも使用できます。  
  
## <a name="next-step"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 8: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)」に進んでください。  
  
  
