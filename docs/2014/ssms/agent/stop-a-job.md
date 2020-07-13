---
title: ジョブの停止 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78986e85dd8ee808f5fb621182d903a94bbc5eb7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067518"
---
# <a name="stop-a-job"></a>Stop a Job
  このトピックでは、エージェントジョブを停止する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 ジョブとは、SQL Server エージェントで実行される特定の一連の処理のことです。  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **ジョブを停止する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   ジョブで **CmdExec** または **PowerShell**型のステップが現在実行されている場合、実行中のプロセス (MyProgram.exe など) は途中で強制終了されます。 途中で強制終了した場合、そのプロセスによって使用されていたファイルが開いたままになるなど、予期しない結果が発生する可能性があります。  
  
-   マルチサーバー ジョブの場合、STOP 命令はそのジョブのすべてのターゲット サーバーに通知されます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-stop-a-job"></a>ジョブを停止するには  
  
1.  **オブジェクト エクスプローラー**で、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、停止するジョブを右クリックして、 **[ジョブの停止]** をクリックします。  
  
3.  複数のジョブを停止するには、 **[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。 [ジョブの利用状況モニター] で、停止する複数のジョブを選択してから右クリックし、 **[ジョブの停止]** をクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL の使用  
  
### <a name="to-stop-a-job"></a>ジョブを停止するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 詳細については、「 [sp_stop_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql)」を参照してください。  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 管理オブジェクトの使用  

### <a name="to-stop-a-job"></a>ジョブを停止するには
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Stop` クラスの `Job` メソッドを呼び出します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
