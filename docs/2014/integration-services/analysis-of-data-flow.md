---
title: データフローの分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4faa8626fd0237477fb521e5eaacf6afc823fd0e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439499"
---
# <a name="analysis-of-data-flow"></a>データ フローの分析
  [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` データベースビューを使用すると、パッケージのデータフローを分析できます。 このビューは、データ フロー コンポーネントが下流コンポーネントへデータを送信するたびに 1 行表示します。 この情報を使用して、各コンポーネントに送信される行をより詳しく理解できます。  
  
> [!NOTE]  
>  catalog.execution_data_statistics ビューに関する情報を取得するために、ログ レベルは **詳細** に設定する必要があります。  
  
 次の例では、パッケージのコンポーネント間で送信された行の数が表示されます。  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 以下の例では、特定の実行で各コンポーネントによって送信された 1 ミリ秒あたりの行数が計算されます。 計算される値は次のとおりです。  
  
-   **total_rows** - コンポーネントによって送信されたすべての行の合計数  
  
-   **wall_clock_time_ms** -各コンポーネントの実行時間の合計 (ミリ秒単位)  
  
-   **num_rows_per_millisecond** -各コンポーネントによって送信された1ミリ秒あたりの行数  
  
 `HAVING`句は、計算で0除算エラーを防ぐために使用されます。  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 [データ フローのデバッグ](troubleshooting/debugging-data-flow.md)  
  
 [パッケージ実行のトラブルシューティング ツール](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a>関連項目  
 [データ フロー内のデータ](data-flow/data-in-data-flows.md)  
  
  
