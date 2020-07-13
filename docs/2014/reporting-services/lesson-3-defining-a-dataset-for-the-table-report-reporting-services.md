---
title: 'レッスン 3 : テーブル レポートのデータセットの定義 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4c78328e02215520b8d33213e01871f010f62d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108461"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>レッスン 3 : テーブル レポートのデータセットの定義 (Reporting Services)
  データ ソースを定義した後、データセットを定義する必要があります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、レポートで使用するデータは *データセット*に格納されます。 データセットには、データ ソースへのポインターと、レポートで使用されるクエリ、および計算フィールドと変数が含まれています。  
  
 レポート デザイナーでクエリ デザイナーを使用すると、クエリをデザインできます。 このチュートリアルでは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] **2008**データベースから販売注文情報を取得するクエリを作成します。  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>レポート データ用に Transact-SQL クエリを定義するには  
  
1.  **レポートデータ**ペインで、[**新規作成**] をクリックし、[**データセット...**] をクリックします。[**データセットのプロパティ**] ダイアログボックスが表示されます。  
  
2.  **[名前]** ボックスに「 **AdventureWorksDataset**」と入力します。  
  
3.  **[レポートに埋め込まれたデータセットを使用します]** をクリックします。  
  
4.  データソース AdventureWorks2012 の名前が [**データソース**] ボックスに表示されていること、および [**クエリの種類**] が [**テキスト**] であることを確認します。  
  
5.  **[クエリ]** ボックスに次の Transact-SQL クエリを入力するか、コピーして貼り付けます。  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  (省略可能) **[クエリ デザイナー]** ボタンをクリックします。 クエリは、テキスト ベースのクエリ デザイナーに表示されます。 **[テキストとして編集]** をクリックすると、グラフィカル クエリ デザイナーに切り替えることができます。 クエリデザイナーのツールバーの [実行] **(!)** ボタンをクリックして、クエリの結果を表示します。  
  
     [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースの 4 つの異なるテーブルの 6 個のフィールドから取得したデータが表示されます。 クエリでは、エイリアスなど Transact-SQL の機能が利用されます。 たとえば、SalesOrderHeader テーブルは soh と呼ばれます。  
  
     **[OK]** をクリックしてクエリ デザイナーを終了します。  
  
7.  **[OK]** をクリックして **[データセットのプロパティ]** ダイアログ ボックスを閉じます。  
  
     レポート データ ペインに **AdventureWorksDataset** データセットとフィールドが表示されます。  
  
## <a name="next-task"></a>次の作業  
 これで、レポートのデータを取得するクエリを指定できました。 次に、レポートのレイアウトを作成します。 「[レッスン 4: レポートへのテーブルの追加 &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポートデザイナー SQL Server Data Tools のクエリデザインツール &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [SSRS&#41;&#40;の接続の種類の SQL Server](report-data/sql-server-connection-type-ssrs.md)   
 [チュートリアル: Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
