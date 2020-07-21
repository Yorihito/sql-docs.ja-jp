---
title: '[SQL 実行タスクエディター] ([パラメーターマッピング] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfbb4468cb69947dfa54fb519b7698286393d578
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437369"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a>[SQL 実行タスク エディター] ([パラメーター マッピング] ページ)
  **[SQL 実行タスク エディター]** ダイアログ ボックスの **[パラメーター マッピング]** ページを使用すると、SQL ステートメント内のパラメーターに変数をマップできます。  
  
 この手順の詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **変数名**  
 [**追加**] をクリックしてパラメーターマッピングを追加した後、システム変数またはユーザー定義変数を一覧から選択するか、[ \<**New variable...**> 変数の**追加**] ダイアログボックスを使用して新しい変数を追加します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)  
  
 **方向**  
 パラメーターの方向を選択します。 各変数を入力パラメーター、出力パラメーター、またはリターン コードにマップします。  
  
 **[データ型]**  
 パラメーターのデータ型を選択します。 使用できるデータ型の一覧は、タスクによって使用される接続マネージャーで選択したプロバイダーに固有のものです。  
  
 **パラメーター名**  
 パラメーター名を指定します。  
  
 タスクで使用される接続マネージャーの種類によって、数字またはパラメーター名を使用する必要があります。 接続マネージャーの種類によっては、パラメーター名の先頭文字を \@ 記号にすること、\@Param1 などの特定の名前を使用すること、またはパラメーター名として列名を使用することが求められます。  
  
 **関連トピック:** [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **[パラメーター サイズ]**  
 文字列やバイナリ フィールドなどの可変長パラメーターのサイズを指定します。  
  
 この設定により、プロバイダーは可変長パラメーター値に十分な領域を割り当てることができるようになります。  
  
 **[追加]**  
 クリックすると、パラメーター マッピングが追加されます。  
  
 **[削除]**  
 一覧からパラメーター マッピングを選択してから **[削除]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[SQL 実行タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[SQL 実行タスクエディター &#40;結果セット] ページ&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](/sql/t-sql/language-reference)  
  
  
