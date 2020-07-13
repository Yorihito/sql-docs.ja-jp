---
title: クエリパラメーターを SQL 実行タスクの変数にマップする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2e105e2ccccce912965cbfc0662a380ea1a6264
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440269"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a>クエリ パラメーターを SQL 実行タスクの変数にマップする方法

  このトピックでは、SQL 実行タスクでパラメーター化された SQL ステートメントを使用して、SQL ステートメント内の変数とパラメーター間のマッピングを作成する方法を説明します。  
  
 異なる種類の接続で使用する SQL 実行タスク、パラメーター マーカー、およびパラメーター名の詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」および「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>クエリ パラメーターを変数にマップするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、操作する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックします。  
  
4.  SQL 実行タスクがまだパッケージに含まれていない場合、SQL 実行タスクをパッケージの制御フローに追加します。 詳細については、「[制御フローでのタスクまたはコンテナーの追加または削除](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。  
  .  
  
5.  SQL 実行タスクをダブルクリックします。  
  
6.  パラメーター化 SQL コマンドを、次のいずれかの方法で指定します。  
  
    -   直接入力を使用して、SQLStatement プロパティに SQL コマンドを入力します。  
  
    -   直接入力を使用して、 **[クエリの作成]** をクリックし、クエリ ビルダーで用意されているグラフィック ツールを使用して、SQL コマンドを作成します。  
  
    -   ファイル接続を使用し、SQL コマンドが含まれるファイルを参照します。  
  
    -   変数を使用し、SQL コマンドが含まれる変数を参照します。  
  
     パラメーター化された SQL ステートメントで使用するパラメーター マーカーは、SQL 実行タスクが使用する接続の種類によって異なります。  
  
    |接続の種類|パラメーター マーカー|  
    |---------------------|----------------------|  
    |ADO (ADO)|?|  
    |ADO.NET および SQLMOBILE|@\<parameter name>|  
    |ODBC|?|  
    |EXCEL および OLE DB|?|  
  
     次の表に、SELECT コマンドの例を接続マネージャーの種類別に示します。 パラメーターは、WHERE 句で使用されるフィルター値を提供します。 この例では、SELECT を使用して、2 つのパラメーターで指定された値よりも **ProductID** の値が大きい製品と小さい製品を、 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] の **Product** テーブルから返します。  
  
    |接続の種類|SELECT 構文|  
    |---------------------|-------------------|  
    |EXCEL、ODBC、OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |ADO (ADO)|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     ストアド プロシージャでパラメーターを使用する例については、「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。  
  
7.  **[パラメーター マッピング]** をクリックします。  
  
8.  パラメーター マッピングを追加するには、 **[追加]** をクリックします。  
  
9. **[パラメーター名]** ボックスに名前を入力します。  
  
     使用するパラメーター名は、SQL 実行タスクが使用する接続の種類によって異なります。  
  
    |接続の種類|パラメーター名|  
    |---------------------|--------------------|  
    |ADO (ADO)|Param1、Param2、...|  
    |ADO.NET および SQLMOBILE|@\<parameter name>|  
    |ODBC|1、2、3、...|  
    |EXCEL および OLE DB|0、1、2、3、…|  
  
10. **[変数名]** 一覧で、変数を選択します。 詳細については、「 [パッケージ内のユーザー定義変数のスコープの追加、削除、変更](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)」を参照してください。  
  
11. **[方向]** 一覧で、パラメーターが入力、出力、または戻り値のいずれであるかを指定します。  
  
12. **[データ型]** 一覧で、パラメーターのデータ型を設定します。  
  
    > [!IMPORTANT]  
    >  パラメーターのデータ型は、変数のデータ型と互換性がある必要があります。  
  
13. SQL ステートメントの各パラメーターに対して、手順 8. ～ 11. を繰り返します。  
  
    > [!IMPORTANT]  
    >  パラメーター マッピングの順序は、SQL ステートメントで使用されるパラメーターの順序と同じである必要があります。  
  
14. **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL 実行タスク](control-flow/execute-sql-task.md)   
 [SQL 実行タスクのパラメーターとリターンコード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)   
 [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)  
  
  
