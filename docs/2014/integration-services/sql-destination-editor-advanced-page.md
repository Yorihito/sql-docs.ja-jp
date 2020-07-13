---
title: SQL 変換先エディター ([詳細設定] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 916de5dabdc64c22821a4984b8632baa0d9515b8
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421149"
---
# <a name="sql-destination-editor-advanced-page"></a>[SQL 変換先エディター] ([詳細設定] ページ)
  **[SQL 変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、詳細な一括挿入オプションを指定できます。  
  
 SQL Server 変換先の詳細については、「 [SQL Server Destination](data-flow/sql-server-destination.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[ID を保持する]**  
 タスクが値を ID 列に挿入するかどうかを指定します。 このプロパティの既定値は `False` です。  
  
 **[NULL を保持する]**  
 タスクが NULL 値を保持するかどうかを指定します。 このプロパティの既定値は `False` です。  
  
 **テーブルロック**  
 データが読み込まれるときにテーブルをロックするかどうかを指定します。 このプロパティの既定値は `True` です。  
  
 **CHECK 制約**  
 タスクが制約をチェックするかどうかを指定します。 このプロパティの既定値は `True` です。  
  
 **[トリガーを起動する]**  
 テーブルにおける一括挿入でトリガーを起動するかどうかを指定します。 このプロパティの既定値は `False` です。  
  
 **[先頭行]**  
 先頭行が挿入されるように指定します。 このプロパティの既定値は、 **-1**です。これは、値が割り当てられていないことを示します。  
  
> [!NOTE]  
>  このプロパティに値を割り当てない場合、 **[SQL 変換先エディター]** のテキスト ボックスをクリアします。 **[プロパティ]** ウィンドウ、 **[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。  
  
 **[最終行]**  
 最終行が挿入されるように指定します。 このプロパティの既定値は、 **-1**です。これは、値が割り当てられていないことを示します。  
  
> [!NOTE]  
>  このプロパティに値を割り当てない場合、 **[SQL 変換先エディター]** のテキスト ボックスをクリアします。 **[プロパティ]** ウィンドウ、 **[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。  
  
 **エラーの最大数**  
 一括挿入を停止する前に許容するエラー数を指定します。 このプロパティの既定値は、 **-1**です。これは、値が割り当てられていないことを示します。  
  
> [!NOTE]  
>  このプロパティに値を割り当てない場合、 **[SQL 変換先エディター]** のテキスト ボックスをクリアします。 **[プロパティ]** ウィンドウ、 **[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。  
  
 **タイムアウト**  
 タイムアウトで一括挿入が停止されるまでの待機時間を秒数で指定します。  
  
 **[列の順序]**  
 キー列の名前を入力します。 各列は、昇順または降順で並べ替えることができます。 複数のキー列を使用する場合は、リストをコンマで区切ります。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[SQL 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md)   
 [SQL 変換先エディター &#40;マッピングページ&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [SQL Server 変換先を使用してデータの一括読み込みを行う](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
