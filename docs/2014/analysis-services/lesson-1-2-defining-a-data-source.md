---
title: データソースの定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: b206facd1a8dc3faa58c58ae97e783d8a5c630b6
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543624"
---
# <a name="defining-a-data-source"></a>データ ソースの定義
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを作成した後は、通常、そのプロジェクトで使用するデータ ソースを 1 つ以上定義します。 データ ソースを定義するときは、データ ソースへの接続に使用する接続文字列情報を定義します。 詳細については、「 [データ ソースの作成 &#40;SSAS 多次元&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md)」を参照してください。  
  
 次の実習では、AdventureWorksDWSQLServer2012 サンプル データベースを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトのデータ ソースとして定義します。 チュートリアル用にサンプル データベースはローカル コンピューターに保存されていますが、ソース データベースから 1 つ以上のリモート コンピューターをホストすることもしばしばあります。  
  
### <a name="to-define-a-new-data-source"></a>新しいデータ ソースを定義するには  
  
1.  ソリューション エクスプローラー (Microsoft Visual Studio ウィンドウの右側) で、 **[データ ソース]** を右クリックし、 **[新しいデータ ソース]** をクリックします。  
  
2.  **データ ソース ウィザード** の **[データ ソース ウィザードへようこそ]** ページで、 **[次へ]** をクリックして **[接続の定義方法を選択します]** ページを開きます。  
  
3.  **[接続の定義方法を選択します]** ページでは、新しい接続、既存の接続、または以前に定義したデータ ソース オブジェクトに基づいて、データ ソースを定義できます。 ここでは、新しい接続に基づいてデータ ソースを定義します。 **[既存の接続または新しい接続に基づいてデータ ソースを作成する]** が選択されていることを確認し、 **[新規作成]** をクリックします。  
  
4.  **[接続マネージャー]** ダイアログ ボックスで、データ ソースの接続のプロパティを定義します。 **[プロバイダー]** ボックスの一覧で、 **[ネイティブ OLE DB\SQL Server Native Client 11.0]** が選択されていることを確認します。  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、 **[プロバイダー]** ボックスの一覧に表示されるその他のプロバイダーもサポートしています。  
  
5.  [**サーバー名**] テキストボックスに、「」と入力 `localhost` します。  
  
     ローカルコンピューター上の名前付きインスタンスに接続するには、 **localhost \\<インスタンス \> 名**を入力します。 ローカル コンピューターではなく指定のコンピューターに接続するには、コンピューター名または IP アドレスを入力します。  
  
6.  **[Windows 認証を使用]** が選択されていることを確認します。 **[データベースの選択または入力]** ボックスの一覧で、 **[AdventureWorksDW2012]** を選択します。  
  
7.  **[接続テスト]** をクリックして、データベースへの接続をテストします。  
  
8.  [**OK**] をクリックし、[**次へ**] をクリックします。  
  
9. ウィザードの **[権限借用情報]** ページでは、データ ソースへの接続時に使用する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のセキュリティ資格情報を定義します。 権限借用は、Windows 認証が選択されている場合に、データ ソースへの接続に使用される Windows アカウントに関連する機能です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、OLAP オブジェクトを処理するための権限借用はサポートされていません。 **[サービス アカウントを使用する]** をクリックし、 **[次へ]** をクリックします。  
  
10. **[ウィザードの完了]** ページで、既定の名前である **Adventure Works DW 2012**をそのまま使用して、 **[完了]** をクリックします。新しいデータ ソースが作成されます。  
  
> [!NOTE]  
>  作成後にデータ ソースのプロパティを変更するには、 **[データ ソース]** フォルダー内のデータ ソースをダブルクリックします。 **[データ ソース デザイナー]** にデータ ソースのプロパティが表示されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [データ ソース ビューの定義](lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a>参照  
 [データ ソースの作成 &#40;SSAS 多次元&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
  
