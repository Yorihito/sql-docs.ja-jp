---
title: テーブルの別名の作成
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: b89cec27a4c31b8165129fe4b3565ce6f448ac15
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999988"
---
# <a name="create-table-aliases-visual-database-tools"></a>テーブルの別名の作成 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
別名を使用すると、テーブル名を使った操作が容易になります。 別名は、次の場合に使用すると便利です。  
  
-   [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) のステートメントを短くして、読みやすくする場合。  
  
-   クエリでテーブル名を列名の修飾などに頻繁に参照する場合で、クエリの文字数を一定文字数にする場合。 一部のデータベースでは、クエリの最大文字数が決まっています。  
  
-   自己結合などで同一テーブルの複数のインスタンスを使用し、いずれかのインスタンスを参照する方法が必要な場合。  
  
たとえば、テーブル名 `employee_information` に対して別名 `"e"` を作成すると、クエリの残りの部分でテーブルを `"e"` として参照できます。  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>テーブルまたはテーブル値オブジェクトの別名を作成するには  
  
1.  クエリにテーブルまたはテーブル値オブジェクトを追加します。  
  
2.  **ダイアグラム ペイン**で、別名を作成するオブジェクトを右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。  
  
3.  **[プロパティ]** ウィンドウの **[エイリアス]** フィールドに別名を入力します。  
  
## <a name="see-also"></a>参照  
[クエリへのテーブルの追加 (Visual Database Tools)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
