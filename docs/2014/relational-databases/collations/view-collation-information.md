---
title: 照合順序情報の表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 995e559cfd7ca871f5abd90751f2f79167bdf76f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970556"
---
# <a name="view-collation-information"></a>照合順序情報の表示
    
##  <a name="you-can-view-the-collation-of-a-server-database-or-column-in-ssmanstudiofull-using-object-explorer-menu-options-or-by-using-tsql"></a><a name="Top"></a> サーバー、データベース、または列の照合順序は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプローラーのメニュー オプションを使用するか、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して表示できます。  
  
##  <a name="how-to-view-a-collation-setting"></a><a name="Procedures"></a> 照合順序の設定を表示する方法  
 次のいずれかを使用します。  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **サーバー (SQL Server のインスタンス) の照合順序設定をオブジェクト エクスプローラーで表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  インスタンスを右クリックし、 **[プロパティ]** をクリックします。  
  
 **データベースの照合順序設定をオブジェクト エクスプローラーで表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、データベースを右クリックして、 **[プロパティ]** をクリックします。  
  
 **列の照合順序設定をオブジェクト エクスプローラーで表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、データベースを展開して、 **[テーブル]** を展開します。  
  
3.  目的の列を含んだテーブルを展開し、 **[列]** を展開します。  
  
4.  列を右クリックし、 **[プロパティ]** をクリックします。 照合順序プロパティが空の場合、列が文字データ型ではありません。  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 **サーバーの照合順序設定を表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。  
  
2.  クエリ ウィンドウで、SERVERPROPERTY システム関数を使用した次のステートメントを入力します。  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  また、sp_helpsort システム ストアド プロシージャを使用することもできます。  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 **サポートされているすべての照合順序を表示するには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。  
  
2.  クエリ ウィンドウで、SERVERPROPERTY システム関数を使用した次のステートメントを入力します。  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **データベースの照合順序設定を表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。  
  
2.  クエリ ウィンドウで、sys.databases システム カタログ ビューを使用した次のステートメントを入力します。  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  また、DATABASEPROPERTYEX システム関数を使用することもできます。  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **列の照合順序設定を表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、ツール バーの **[新しいクエリ]** をクリックします。  
  
2.  クエリ ウィンドウで、sys.columns システム カタログ ビューを使用した次のステートメントを入力します。  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a>参照  
 [SERVERPROPERTY &#40;Transact-sql&#41;](/sql/t-sql/functions/serverproperty-transact-sql)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [&#40;Transact-sql&#41;の列](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)   
 [照合順序の優先順位 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql)   
 [sp_helpsort &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
