---
title: テーブルの作成 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d84a4da6a10fbcbae311fe1bf738c03b85a4c6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056830"
---
# <a name="create-tables-database-engine"></a>テーブルの作成 (データベース エンジン)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して新しいテーブルを作成して名前を付け、それを既存のデータベースに追加できます。

> [!NOTE]
>  SQL Azure データベースに接続している場合、[新しいテーブル] オプションを選択すると、テーブルの作成テンプレート スクリプトが実行されます。 パラメーターを編集してから、このスクリプトを実行して新しいテーブルを作成してください。 詳細については、「 [SQL Azure の概要](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx)」を参照してください。

 **このトピックの内容**

-   **作業を開始する準備:**

     [Security](#Security)

-   **テーブルを作成する方法:**

     [SQL Server Management Studio](#SSMSProcedure)

     [Transact-SQL](#TsqlProcedure)

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに

###  <a name="security"></a><a name="Security"></a> セキュリティ

####  <a name="permissions"></a><a name="Permissions"></a> Permissions
 データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。

 CREATE TABLE ステートメント内の列を CLR ユーザー定義型として定義する場合は、その型の所有権か、その型に対する REFERENCES 権限が必要です。

 CREATE TABLE ステートメント内の列に XML スキーマ コレクションが関連付けられている場合は、その XML スキーマ コレクションの所有権か、そのスキーマ コレクションに対する REFERENCES 権限が必要です。

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用

#### <a name="to-create-a-table-with-table-designer"></a>テーブル デザイナーでテーブルを作成するには

1.  **オブジェクト エクスプローラー**で、変更するデータベースを含む [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。

2.  **オブジェクト エクスプローラー**で、 **[データベース]** ノードを展開し、新しいテーブルを格納するデータベースを展開します。

3.  オブジェクト エクスプローラーで、データベースの **[テーブル]** ノードを右クリックし、 **[新しいテーブル]** をクリックします。

4.  次の図に示すように、列名を入力し、データ型を選択した後、各列で null 値を許可するかどうかを選択します。

     ![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")

5.  他のプロパティ (ID 列または計算列の値など) を指定するには、列をクリックし、列のプロパティ タブで適切なプロパティを選択します。 列のプロパティの詳細については、「[テーブル列のプロパティ &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md)」を参照してください。

6.  列を主キーとして指定するには、列を右クリックし、 **[主キーの設定]** をクリックします。 詳細については、「 [Create Primary Keys](../tables/create-primary-keys.md)」を参照してください。

7.  外部キーのリレーションシップ、CHECK 制約、またはインデックスを作成するには、テーブル デザイナー ペイン内で右クリックし、次の図に示すように、一覧からオブジェクトを選択します。

     ![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")

     これらのオブジェクトの詳細については、「 [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md)」、「 [Create Check Constraints](../tables/create-check-constraints.md) 」、および「 [Indexes](../indexes/indexes.md)」を参照してください。

8.  既定では、テーブルは **dbo** スキーマに含まれています。 テーブルに対して別のスキーマを指定するには、テーブル デザイナー ペイン内で右クリックし、次の図に示すように、 **[プロパティ]** を選択します。 **[スキーマ]** ボックスの一覧で、適切なスキーマを選択します。

     ![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")

     スキーマの詳細については、「 [Create a Database Schema](../security/authentication-access/create-a-database-schema.md)」を参照してください。

9. [**ファイル**] メニューの [ **Save** *テーブル名*の保存] をクリックします。

10. **[名前の選択]** ダイアログ ボックスで、テーブルの名前を入力し、 **[OK]** をクリックします。

11. 新しいテーブルを表示するには、 **オブジェクト エクスプローラー**で、 **[テーブル]** ノードを展開し、 **F5** キーを押してオブジェクトの一覧を更新します。 新しいテーブルがテーブルの一覧に表示されます。

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用

#### <a name="to-create-a-table-in-the-query-editor"></a>クエリ エディターでテーブルを作成するには

1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。

2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。

3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。

    ```
    CREATE TABLE dbo.PurchaseOrderDetail
    (
        PurchaseOrderID int NOT NULL
        ,LineNumber smallint NOT NULL
        ,ProductID int NULL
        ,UnitPrice money NULL
        ,OrderQty smallint NULL
        ,ReceivedQty float NULL
        ,RejectedQty float NULL
        ,DueDate datetime NULL
    );
    ```

 詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」を参照してください。


