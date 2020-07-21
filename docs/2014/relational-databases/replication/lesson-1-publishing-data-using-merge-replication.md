---
title: 'レッスン 1 : マージ レプリケーションを使用したデータのパブリッシュ | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
author: rothja
ms.author: jroth
ms.openlocfilehash: 30d7c1e04c305a74f99d5d2818b344bfd8f83bd1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065989"
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a>レッスン 1 : マージ レプリケーションを使用したデータのパブリッシュ
   このレッスンでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してマージ パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Employee** テーブル、**SalesOrderHeader** テーブル、および **SalesOrderDetail** テーブルのサブセットをパブリッシュします。 ここでは、パラメーター化された行フィルターを使ってこれらのテーブルをフィルター処理し、サブスクリプションごとに一意のデータ部分が含まれるようにします。 また、マージ エージェントにより使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインをパブリケーション アクセス リスト (PAL) に追加します。 このチュートリアルを学習するには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。  
  
### <a name="to-create-a-publication-and-define-articles"></a>パブリケーションを作成し、アーティクルを定義するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** を右クリックして、 **[新しいパブリケーション]** をクリックします。  
  
     パブリケーションの新規作成ウィザードが起動します。  
  
3.  [パブリケーション データベース] ページで [ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、 **[次へ]** をクリックします。  
  
4.  [パブリケーションの種類] ページで、 **[マージ パブリケーション]** を選択し、 **[次へ]** をクリックします。  
  
5.  [サブスクライバーの種類] ページで、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のみが選択されていることを確認し、 **[次へ]** をクリックします。  
  
6.  [アーティクル] ページで、 **[テーブル]** ノードを展開して **[SalesOrderHeader]** および **[SalesOrderDetail]** を選択します。次に **[Employee]** を展開し、 **[EmployeeID]** または **[LoginID]** を選択して、 **[次へ]** をクリックします。  
  
    > [!TIP]  
    >  その他の必要な列が自動的に選択されます。 自動的に選択された列のいずれかを選択すると、 **[パブリッシュするオブジェクト]** の一覧の下に、その列が必要な理由についての説明が表示されます。  
  
7.  [テーブル行のフィルター選択] ページで、 **[追加]** をクリックして **[フィルターの追加]** をクリックします。  
  
8.  **[フィルターの追加]** ダイアログ ボックスの **[フィルターを適用するテーブルを選択します。]** で **[Employee (HumanResources)]** を選択します。 **[LoginID]** 列をクリックして、右矢印をクリックし、フィルター選択クエリの WHERE 句にこの列を追加します。WHERE 句を次のように修正します。  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** をクリックして、 **[OK]** をクリックします。  
  
10. **[テーブル行のフィルター選択]** ページで、 **[Employee (Human Resources)]**、 **[追加]** の順にクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。  
  
11. **[結合の追加]** ダイアログ ボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderHeader]** をクリックして、 **[JOIN ステートメントを手動で作成する]** をクリックし、JOIN ステートメントを次のように完成させます。  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. **[結合オプションを指定します]** で、 **[一意キー]** を選択して **[OK]** をクリックします。  
  
13. [テーブル行のフィルター選択] ページで、 **[SalesOrderHeader]**、 **[追加]** の順にクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。  
  
14. **[結合の追加]** ダイアログ ボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderDetail]** をクリックします。  
  
15. **[JOIN ステートメントを手動で作成する]** をクリックします。  
  
16. **[フィルター選択されたテーブルの列]** で、 **[BusinessEntityID]** を選択し、矢印ボタンをクリックして列名を JOIN ステートメントにコピーします。  
  
17. **[JOIN ステートメント]** ボックスで、次のように JOIN ステートメントを完成させます。  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. **[結合オプションを指定します]** で、 **[一意キー]** を選択して **[OK]** をクリックします。  
  
19. **[テーブル行のフィルター選択]** ページで、 **[SalesOrderHeader (Sales)]**、 **[追加]** の順にクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。  
  
20. **[結合の追加]** ダイアログボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderDetail]** をクリックして **[OK]** をクリックし、 **[次へ]** をクリックします。  
  
21. **[スナップショットをすぐに作成する]** を選択し、 **[以下のスケジュールでスナップショット エージェントを実行する]** をオフにして、 **[次へ]** をクリックします。  
  
22. [エージェントセキュリティ] ページで、[**セキュリティ設定**] をクリックし、[ \<_Machine_Name> **プロセスアカウント**] ボックスに「_**\ repl_snapshot** 」と入力して、このアカウントのパスワードを入力し、[ **OK]** をクリックします。 **[完了]** をクリックします。  
  
23. [ウィザードの完了] ページで、 **[パブリケーション名]** ボックスに「 **AdvWorksSalesOrdersMerge** 」と入力し、 **[完了]** をクリックします。  
  
24. パブリケーションが作成されたら、 **[閉じる]** をクリックします。  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>スナップショット生成の状態を表示するには  
  
1.  でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。  
  
2.  [ローカル パブリケーション] フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** を右クリックして、 **[スナップショット エージェントの状態の表示]** をクリックします。  
  
3.  パブリケーションのスナップショット エージェントの現在の状態が表示されるので、 スナップショット ジョブが正常に終了していることを確認してから次のレッスンに進みます。  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>マージ エージェントのログインを PAL に追加するには  
  
1.  でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。  
  
2.  [ローカル パブリケーション] フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、 **[プロパティ]** をクリックします。  
  
     **[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[パブリケーション アクセス リスト]** ページを選択して、 **[追加]** をクリックします。  
  
4.  [パブリケーション アクセスの追加] ダイアログ ボックスで、_<コンピューター名>_**\repl_merge** を選択して **[OK]** をクリックします。 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、マージ パブリケーションを作成しました。 次は、このパブリケーションをサブスクライブします。 「 [レッスン 2: マージ パブリケーションへのサブスクリプションの作成](lesson-2-creating-a-subscription-to-the-merge-publication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パブリッシュされたデータのフィルター処理](publish/filter-published-data.md)   
 [パラメーター化された行フィルター](merge/parameterized-filters-parameterized-row-filters.md)   
 [アーティクルの定義](publish/define-an-article.md)  
  
  
