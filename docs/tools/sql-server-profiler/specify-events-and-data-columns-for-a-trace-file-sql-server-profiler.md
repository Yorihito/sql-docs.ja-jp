---
title: トレース ファイルに含めるイベントとデータ列を指定する
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 9c4ba5002eab9fd0c495d19aa662c1252824a445
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307723"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a>トレース ファイルに含めるイベントとデータ列の指定 (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してトレースに含めるイベント クラスとデータ列を指定する方法について説明します。  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a>トレースに含めるイベントとデータ列を指定するには  
  
1.  **[トレースのプロパティ]** または **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。  
  
     **[イベントの選択]** タブにはグリッド コントロールがあります。 グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。 このテーブルには、各イベント クラスが 1 行で表示されます。 表示されるイベント クラスは、接続しているサーバーの種類とバージョンによって多少異なります。 イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別に分類されています。 残りの列には、各イベント クラスに対応するデータ列が表示されます。  
  
2.  **[イベントの選択]** タブで、グリッド コントロールを使用して、トレース ファイルに対するイベントとデータ列の追加または削除を行います。  
  
3.  トレースからイベントを削除するには、各イベント クラスの **[Events]** 列のチェック ボックスをオフにします。  
  
4.  トレースにイベントを含めるには、各イベント クラスの **[Events]** 列のチェック ボックスをオンにするか、イベントに対応するデータ列のチェック ボックスをオンにします。  
  
> [!IMPORTANT]  
>  このトレースをシステム モニターやパフォーマンス モニターのデータと関連付ける場合は、 **Start Time** データ列と **End Time** データ列の両方をトレースに含める必要があります。  
  
 イベント クラスを含める場合、イベントに対応するイベント クラスのチェック ボックスをオンにしていると、関連するデータ列もすべてトレースに含まれます。 特定の列のチェック ボックスをオンにしている場合は、その列だけがトレースに含まれます。  
  
1.  イベント クラスからデータ列を削除するには、イベント クラス行のデータ列のチェック ボックスをオフにするか、列ヘッダーを右クリックして、 **[列の選択解除]** をクリックします。  
  
2.  必要に応じて、トレースにフィルターを適用します。 詳細については、「[トレース内のイベントへのフィルターの適用 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
