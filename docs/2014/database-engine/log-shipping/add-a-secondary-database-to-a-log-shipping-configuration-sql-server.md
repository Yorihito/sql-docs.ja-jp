---
title: ログ配布構成へのセカンダリ データベースの追加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 062df1b53ed74321ba0c75c9df763de79a4802bd
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931393"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a>ログ配布構成へのセカンダリ データベースの追加 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、既存のログ配布構成にセカンダリ データベースを追加する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **以下を使用してログ配布セカンダリ データベースを追加するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a>ログ配布セカンダリ データベースを追加するには  
  
1.  ログ配布構成のプライマリ データベースとして使用するデータベースを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[ページの選択]** の **[トランザクション ログの配布]** をクリックします。  
  
3.  **[セカンダリ サーバー インスタンスとデータベース]** の **[追加]** をクリックします。  
  
4.  **[接続]** をクリックし、セカンダリ サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。  
  
5.  **[セカンダリ データベース]** ボックスで、一覧からデータベースを選択するか、作成するデータベースの名前を入力します。  
  
6.  **[セカンダリ データベースの初期化]** タブで、セカンダリ データベースを初期化するためのオプションを選択します。  
  
7.  **[ファイルのコピー]** タブの **[ファイルのコピー先フォルダー]** に、トランザクション ログ バックアップのコピー先フォルダーのパスを入力します。 多くの場合、セカンダリ サーバー上のフォルダーを指定します。  
  
8.  **[復元ジョブ]** の **[スケジュール]** ボックスにコピー スケジュールの一覧が表示されます。 スケジュールをカスタマイズする場合、 **[スケジュール]** をクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。 このスケジュールはバックアップ スケジュールに近い設定にします。  
  
9. **[復元]** タブの **[バックアップ復元時のデータベース状態]** で、 **[復旧モードなし]** または **[スタンバイ モード]** を選択します。  
  
10. **[スタンバイ モード]** を選択する場合は、復元操作の進行中にセカンダリ データベースからユーザーを切断するかどうかを選択します。  
  
11. セカンダリ サーバーの復元処理を遅延させる場合、 **[バックアップの復元を最低限次の期間遅延する]** で遅延時間を選択します。  
  
12. **[復元が次の期間内に行われない場合は警告する]** で警告のしきい値を選択します。  
  
13. **[復元ジョブ]** の **[スケジュール]** ボックスに表示される復元スケジュールを確認します。 スケジュールをカスタマイズする場合、 **[スケジュール]** をクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。 このスケジュールはバックアップ スケジュールに近い設定にします。  
  
14. **[OK]** をクリックします。  
  
15. [データベースのプロパティ] ダイアログ ボックスの **[OK]** をクリックして、構成処理を開始します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a>ログ配布セカンダリ データベースを追加するには  
  
1.  セカンダリ サーバーで [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) を実行します。このとき、プライマリ サーバーとプライマリ データベースの詳細情報を指定します。 このストアド プロシージャからは、セカンダリ ID、コピー ジョブ ID、および復元ジョブ ID が返されます。  
  
2.  セカンダリ サーバーで [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) を実行して、コピー ジョブと復元ジョブのスケジュールを設定します。  
  
3.  セカンダリ サーバーで [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを追加します。  
  
4.  プライマリ サーバーで [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) を実行して、新しいセカンダリ データベースに関する必要な情報をプライマリ サーバーに追加します。  
  
5.  セカンダリ サーバーでコピー ジョブと復元ジョブを有効にします。 詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [ログ配布の構成 &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)  
  
-   [ログ配布構成からのセカンダリ データベースの削除 &#40;SQL Server&#41;](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [ログ配布の削除 &#40;SQL Server&#41;](remove-log-shipping-sql-server.md)  
  
-   [ログ配布レポートの表示 &#40;SQL Server Management Studio&#41;](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [ログ配布の監視 &#40;Transact-SQL&#41;](monitor-log-shipping-transact-sql.md)  
  
-   [ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md)   
 [Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md)  
  
  
