---
title: 翻訳の定義と参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9fb624116ca42f32ab20615d1c34fcb786d150a1
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542244"
---
# <a name="defining-and-browsing-translations"></a>翻訳の定義と表示
  翻訳とは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のオブジェクトの名前を特定の言語で表現することです。 オブジェクトには、メジャー グループ、メジャー、ディメンション、属性、階層、KPI、アクション、計算されるメンバーなどがあります。 翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。 この場合、クライアントは、ロケール識別子 (LCID) を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに渡します。 のインスタンスはこの LCID に基づいて、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトにメタデータを提供する際に使用する翻訳セットを判別します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトにその言語の翻訳が含まれていない場合、または特定のオブジェクトの翻訳が含まれていない場合は、オブジェクトのメタデータがクライアントに送り返される際に既定の言語が使用されます。 たとえば、フランスのビジネス ユーザーが、フランス語にロケール設定されたワークステーションからキューブにアクセスした場合、該当する項目がフランス語に翻訳されているのであれば、メンバー キャプションとメンバー プロパティ値がフランス語で表示されます。 一方、ドイツのビジネス ユーザーが、ドイツ語にロケール設定されたワークステーションから同じキューブにアクセスすると、メンバー キャプションとメンバー プロパティ値はドイツ語で表示されます。 詳細については、「[ディメンションの翻訳](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)」、「[キューブの翻訳](multidimensional-models-olap-logical-cube-objects/cube-translations.md)」、「[翻訳 &#40;Analysis Services&#41;](translations-analysis-services.md)」を参照してください。  
  
 このトピックの作業では、Date ディメンションのディメンション オブジェクトと [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ オブジェクトの限定されたセットに関するメタデータ翻訳を定義します。 それから、これらのディメンションとキューブ オブジェクトを表示して、メタデータ翻訳を確認します。  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a>Date ディメンションのメタデータの翻訳の指定  
  
1.  **Date** ディメンションのディメンション デザイナーを開き、 **[翻訳]** タブをクリックします。  
  
     各ディメンション オブジェクトの既定の言語でメタデータが表示されます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの既定の言語は英語です。  
  
2.  **[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。  
  
     **[言語の選択]** ダイアログ ボックスに言語の一覧が表示されます。  
  
3.  **[スペイン語 (スペイン)]** をクリックして、 **[OK]** をクリックします。  
  
     新しい列が表示されるので、翻訳対象のメタデータ オブジェクトのスペイン語の翻訳をその列で定義します。 このチュートリアルでは、プロセスを示すために少数のオブジェクトだけを翻訳します。  
  
4.  **[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。 **[言語の選択]** ダイアログ ボックスで **[フランス語 (フランス)]** をクリックして、 **[OK]** をクリックします。  
  
     新しい言語列が表示されるので、フランス語の翻訳をその列で定義します。  
  
5.  **Date**ディメンションの**キャプション**オブジェクトの行で、[ `Fecha` **スペイン語 (スペイン)** ] 翻訳列と [ `Temps` **フランス語 (フランス)** ] 翻訳列に「」と入力します。  
  
6.  **Month Name**属性の**Caption**オブジェクトの行で、 `Mes del Año` **スペイン語 (スペイン)** 翻訳列を入力し、[ `Mois d'Année` **フランス語 (フランス)** ] 翻訳列に「」と入力します。  
  
     これらの翻訳を入力すると、省略記号 (**..**.) が表示されます。 この参照ボタンをクリックすると、属性階層の各メンバーの翻訳を入力する基になるテーブルの列を指定できます。  
  
7.  **Month Name**属性の [**スペイン語 (スペイン)** ] 翻訳の省略記号 (**...**) をクリックします。  
  
     **[属性データの翻訳]** ダイアログ ボックスが表示されます。  
  
8.  次の図のように、 **[翻訳列]** ボックスの一覧で **[SpanishMonthName]** をクリックします。  
  
     ![[属性データの翻訳] ダイアログボックス](../../2014/tutorials/media/l9-translations-4.gif "[属性データの翻訳] ダイアログ ボックス")  
  
9. [ **OK**] をクリックし、 **Month Name**属性の [**フランス語 (フランス)** ] 翻訳の省略記号ボタン ([**...**]) をクリックします。  
  
10. **[翻訳列]** ボックスの一覧で **[FrenchMonthName]** をクリックして、 **[OK]** をクリックします。  
  
     この手順は、ディメンション オブジェクトおよびメンバーのメタデータ翻訳を定義するプロセスを示しています。  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a>Analysis Services Tutorial キューブのメタデータの翻訳の指定  
  
1.  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[翻訳]** タブに切り替えます。  
  
     次の図のように、各キューブ オブジェクトの既定の言語でメタデータが表示されます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの既定の言語は英語です。  
  
     ![[翻訳] タブの既定の言語](../../2014/tutorials/media/l9-translations-5.gif "[翻訳] タブの既定の言語")  
  
2.  **[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。  
  
     **[言語の選択]** ダイアログ ボックスに言語の一覧が表示されます。  
  
3.  **[スペイン語 (スペイン)]** を選択して、 **[OK]** をクリックします。  
  
     新しい列が表示されるので、翻訳対象のメタデータ オブジェクトのスペイン語の翻訳をその列で定義します。 このチュートリアルでは、プロセスを示すために少数のオブジェクトだけを翻訳します。  
  
4.  **[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。 **[言語の選択]** ダイアログ ボックスで **[フランス語 (フランス)]** をクリックして、 **[OK]** をクリックします。  
  
     新しい言語列が表示されるので、フランス語の翻訳をその列で定義します。  
  
5.  **Date**ディメンションの**キャプション**オブジェクトの行で、[ `Fecha` **スペイン語 (スペイン)** ] 翻訳列と [ `Temps` **フランス語 (フランス)** ] 翻訳列に「」と入力します。  
  
6.  **Internet Sales**メジャーグループの**キャプション**オブジェクトの行で、[ `Ventas del lnternet` **スペイン語 (スペイン)** ] 翻訳列と [ `Ventes D'Internet` **フランス語 (フランス)** ] 翻訳列に「」と入力します。  
  
7.  Internet Sales sales Amount メジャーの**キャプション**オブジェクトの行で、[ `Cantidad de las Ventas del Internet` **スペイン語 (スペイン)** ] 翻訳列と [ `Quantité de Ventes d'Internet` **フランス語 (フランス)** ] 翻訳列に「」と入力します。  
  
     この手順は、キューブ オブジェクトのメタデータ翻訳を定義するプロセスを示しています。  
  
## <a name="browsing-the-cube-by-using-translations"></a>翻訳を使用したキューブの表示  
  
1.  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  配置が正常に完了したら、 **[ブラウザー]** タブに切り替えて、 **[再接続]** をクリックします。  
  
3.  **データ** ペインからすべての階層とメジャーを削除して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [パースペクティブ] **ボックスの一覧で [** Tutorial] をクリックします。  
  
4.  メタデータ ペインで、 **[Measures]** 、 **[Internet Sales]** の順に展開します。  
  
     このメジャー グループに **Internet Sales-Sales Amount** メジャー (英語) があることを確認します。  
  
5.  ツール バーの **[言語]** ボックスの一覧で **[スペイン語 (スペイン)]** をクリックします。  
  
     メタデータ ペインのアイテムが再設定されます。 メタデータ ペインのアイテムが再設定されると、Internet Sales-Sales Amount メジャーが [Internet Sales] 表示フォルダーに表示されなくなります。 代わりに、 `Ventas del lnternet` 次の図に示すように、スペイン語ではという名前の新しい表示フォルダーに表示されます。  
  
     ![再読み込みメタデータペイン](../../2014/tutorials/media/l9-translations-6.gif "再読み込みメタデータペイン")  
  
6.  メタデータペインでを右クリックし、[ `Cantidad de las Ventas del Internet` **クエリに追加**] を選択します。  
  
7.  [メタデータ] ペインで、[] を展開し、[ `Fecha` ] を展開**します。** **[** カレンダーの日付] を右クリックし、[**フィルターに追加**] を選択します。  
  
8.  **フィルター** ペインで、フィルター式として **[CY 2007]** を選択します。  
  
9. メタデータ ペインで **[Mes del Ano]** を右クリックし、 **[クエリに追加]** をクリックします。  
  
     次の図のように、月の名前がスペイン語で表示されます。  
  
     ![データ ペインに表示されたスペイン語での月の名前](../../2014/tutorials/media/l9-translations-7.gif "データ ペインに表示されたスペイン語での月の名前")  
  
10. ツール バーの **[言語]** ボックスの一覧で **[フランス語 (フランス)]** をクリックします。  
  
     月の名前がフランス語で表示され、メジャー名もフランス語で表示されます。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 10: 管理ロールの定義](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a>参照  
 [ディメンションの翻訳](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [キューブの翻訳](multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [翻訳 &#40;Analysis Services&#41;](translations-analysis-services.md)  
  
  
