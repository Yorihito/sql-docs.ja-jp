---
title: ユーザー定義関数の実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4446f3b3a132488fdac6e859f30abaca40a193d3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055012"
---
# <a name="execute-user-defined-functions"></a>ユーザー定義関数の実行
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してユーザー定義関数を実行できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **ユーザー定義関数を実行するために使用するもの:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
 Transact-SQL では、 *値* を使用するか、@*parameter_name*=*値.* を使用し、パラメーターを指定できます。 パラメーターは、トランザクションの一部ではないです。そのため、トランザクションが後でロールバックの値にパラメーターが変更された場合、パラメーター戻すことはできません前の値にします。 呼び出し元に返される値は常に、モジュールから戻る時点での値になります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 EXECUTE ステートメントの実行に権限は必要ありませんが、 EXECUTE 文字列内で参照されるセキュリティ保護可能なリソースに対しては権限が必要です。 たとえば、この文字列に INSERT ステートメントが含まれている場合、EXECUTE ステートメントの呼び出し元は対象のテーブルに対する INSERT 権限が必要です。 EXECUTE ステートメントは、モジュール内に含まれている場合でも、検出されるたびに権限が確認されます。 詳細については、「 [EXECUTE &#40;transact-sql&#41;](/sql/t-sql/language-elements/execute-transact-sql) 」を参照してください。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-execute-a-user-defined-function"></a>ユーザー定義関数を実行するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 詳細については、「 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)」を参照してください。  
  
  
