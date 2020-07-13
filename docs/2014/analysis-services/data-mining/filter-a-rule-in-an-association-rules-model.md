---
title: アソシエーションルールモデルでルールをフィルター処理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filtering rules [Analysis Services]
- Mining Model Viewer [Analysis Services], rules
- Rules Viewer
ms.assetid: 26cdba5b-5bf1-439e-80a3-8759774e918b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10f0dff6db48300b276ea586ec358e2f15089e14
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522448"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a>アソシエーション ルール モデルのルールのフィルター選択
  アソシエーション モデルでフィルターを使用して、結果を必要なアソシエーションだけに限定できます。 たとえば、ルールをフィルター選択して、特定の製品を含むルールだけを表示できます。  
  
 データ マイニング デザイナーで、 **アソシエーション ルール ビューアーの** [ルール] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブのコントロールを使用して、表示されるルールをフィルター選択します。  モデルに対するクエリを作成して、特定の値が格納されているアイテムセットだけを表示することもできます。  
  
> [!NOTE]  
>  このオプションは、Microsoft アソシエーション アルゴリズムを使用して作成されたマイニング モデルに対してのみ使用できます。  
  
### <a name="filter-a-rule-in-an-association-model"></a>アソシエーション モデルのルールのフィルター選択  
  
1.  **アソシエーション ルール ビューアー**を使用してマイニング モデルを開きます。 SQL Server Management Studio でマイニング モデルを開くには、モデル名を右クリックして **[参照]** をクリックします。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でマイニング モデルを開くには、モデルを含むマイニング構造をダブルクリックし、 **データ マイニング デザイナー** の **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **アソシエーション ルール ビューアー** の **[ルール]** タブをクリックします。  
  
3.  **[ルールのフィルター]** ボックスにルールの条件を入力します。 たとえば、「Bike Stand」というルールの条件を入力すると、"Bike Stands" も返されます。  
  
     **[ルールのフィルター]** テキスト ボックスでは、.NET 言語で定義されている正規表現を使用できます。 したがって、 `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`のような式を使用できます。 この式は、Helmets と Fenders という単語が任意の順序で含まれる属性を含むすべてのアイテムセットを返します。  
  
4.  **[最小の確率]** では、確率の値を大きくすると表示されるルール数が減り、値を小さくすると表示されるルール数が増えます。  
  
5.  **[最小の重要度]** では、重要度の値を大きくすると表示されるルール数が減り、値を小さくすると表示されるルール数が増えます。  
  
6.  **[表示]** では、 **[属性の名前と値を表示]**、 **[属性名のみ表示]**、 **[属性値のみ表示]** のいずれかのオプションを選択します。  
  
7.  **[最大行数]** では、値を大きくすると指定した条件を満たすルールの総数が増え、値を小さくすると返されるルールの数が制限されます。 ルールは確率の順に並べられるので、確率または重要度に対して指定した条件を満たす余分なルールを除外できます。  
  
8.  **[長い名前を表示する]** チェック ボックスをオンまたはオフにして、ルール名の表示方法を切り替えます。  
  
     これでルールにフィルターが適用され、指定したアイテムを含むルールのみが表示されます。 フィルター条件は、ルール区切り記号 "->" の前または後の属性値に適用されます。  
  
    > [!NOTE]  
    >  ビューアーはマイニング モデルに対するクエリによって最初に作成されるルールの一覧をキャッシュしており、最大行数、確率、重要度、または長い名前の表示を設定することでクエリの条件を変更しない限り、この一覧は更新されません。 したがって、条件を入力しても表示がすぐに更新されない場合は、 **[長い名前を表示する]** チェック ボックスをオンにしてからオフにすることで、強制的にビューアーのデータを更新することができます。  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a>アソシエーション モデルのアイテムセットに対するクエリの作成  
  
-   [結合モデルのクエリ例](association-model-query-examples.md)  
  
## <a name="see-also"></a>参照  
 [マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft アソシエーションルールビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
