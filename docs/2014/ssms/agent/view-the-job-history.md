---
title: ジョブ履歴の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
ms.openlocfilehash: e84fafdaeddb5748a8129cd5d71d667db7e5fa37
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85001693"
---
# <a name="view-the-job-history"></a>View the Job History
  このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、、、または SQL Server 管理オブジェクトを使用して、でエージェントのジョブ履歴ログを表示する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ジョブ履歴ログを表示する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-the-job-history-log"></a>ジョブ履歴ログを表示するには  
  
1.  **オブジェクト エクスプローラー**で、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。  
  
3.  ジョブを右クリックし、 **[履歴の表示]** をクリックします。  
  
4.  ログ ファイル ビューアーにジョブ履歴が表示されます。  
  
5.  ジョブ履歴を更新するには、 **[最新の情報に更新]** をクリックします。 表示する列を少なくするには、 **[フィルター]** ボタンをクリックし、フィルターのパラメーターを入力します。  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-view-the-job-history-log"></a>ジョブ履歴ログを表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 詳細については、「 [sp_help_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql)」を参照してください。  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 管理オブジェクトの使用  
 **ジョブ履歴ログを表示するには**  
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `EnumHistory` クラスの `Job` メソッドを呼び出します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
