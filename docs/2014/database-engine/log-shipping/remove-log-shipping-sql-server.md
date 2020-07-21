---
title: ログ配布の削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], removing
- removing log shipping
- deleting log shipping
ms.assetid: 859373db-c744-4a4b-8479-45163f61e8cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14fdc36c66073e89dcc2014aed4319a2ce78a98f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931123"
---
# <a name="remove-log-shipping-sql-server"></a>ログ配布の削除 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ログ配布を削除する方法を説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してログ配布を削除するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-remove-log-shipping"></a>ログ配布を削除するには  
  
1.  現在のログ配布プライマリ サーバーである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、ログ配布プライマリ データベースを右クリックして **[プロパティ]** をクリックします。  
  
3.  **[ページの選択]** の **[トランザクション ログの配布]** をクリックします。  
  
4.  **[ログ配布構成のプライマリ データベースとして有効にする]** チェック ボックスをオフにします。  
  
5.  **[OK]** をクリックして、このプライマリ データベースからログ配布を削除します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-remove-log-shipping"></a>ログ配布を削除するには  
  
1.  ログ配布プライマリ サーバーで [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) を実行して、セカンダリ データベースに関する情報をプライマリ サーバーから削除します。  
  
2.  ログ配布セカンダリ サーバーで [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを削除します。  
  
    > [!NOTE]  
    >  同じセカンダリ ID を持つセカンダリ データベースが他にない場合は、 **sp_delete_log_shipping_secondary_primary** が **sp_delete_log_shipping_secondary_database** により呼び出され、セカンダリ ID のエントリ、およびコピー ジョブと復元ジョブが削除されます。  
  
3.  ログ配布プライマリ サーバーで **sp_delete_log_shipping_primary_database** を実行して、ログ配布構成に関する情報をプライマリ サーバーから削除します。 これは、バックアップ ジョブも同時に削除します。  
  
4.  ログ配布プライマリ サーバーでバックアップ ジョブを無効にします。 詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。  
  
5.  ログ配布セカンダリ サーバーでコピー ジョブと復元ジョブを無効にします。  
  
6.  必要に応じて、使用しなくなったログ配布セカンダリ データベースをセカンダリ サーバーから削除することもできます。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [ログ配布の構成 &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)  
  
-   [ログ配布構成へのセカンダリ データベースの追加 &#40;SQL Server&#41;](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [ログ配布構成からのセカンダリ データベースの削除 &#40;SQL Server&#41;](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [ログ配布の監視 &#40;Transact-SQL&#41;](monitor-log-shipping-transact-sql.md)  
  
-   [ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md)   
 [ログ配布テーブルとストアド プロシージャ](log-shipping-tables-and-stored-procedures.md)  
  
  
