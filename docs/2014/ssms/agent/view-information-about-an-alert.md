---
title: 警告に関する情報を表示する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee72512a507299e71f13fee689709a9403bb04e4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058659"
---
# <a name="view-information-about-an-alert"></a>View Information About an Alert
  このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントの警告に関する情報を表示する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **警告に関する情報を表示する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 既定では、警告に関する情報を表示できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。 それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-information-about-an-alert"></a>警告に関する情報を表示するには  
  
1.  **オブジェクト エクスプローラー** で、プラス記号をクリックして、警告に関する情報を表示するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[警告]** フォルダーを展開します。  
  
4.  表示する情報がある警告を右クリックし、**[プロパティ]** を選択します。  
  
     [_alert_name_**警告のプロパティ**] ダイアログ ボックスに表示される使用可能なオプションの詳細については、以下を参照してください。  
  
    -   [[アラートのプロパティ]-[新しいアラート &#40;全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [[アラートのプロパティ]-[新しい警告 &#40;応答] ページ&#41;](alert-properties-new-alert-response-page.md)  
  
    -   [[アラートのプロパティ]: [新しい警告 &#40;オプション] ページ&#41;](alert-properties-new-alert-options-page.md)  
  
    -   [[警告のプロパティ] ([履歴] ページ)](alert-properties-history-page.md)  
  
5.  完了したら、[**OK**] をクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-information-about-an-alert"></a>警告に関する情報を表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 詳細については、「 [sp_help_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql)」を参照してください。  
  
  
