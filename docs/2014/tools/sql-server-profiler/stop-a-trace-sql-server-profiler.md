---
title: トレースの停止 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 501ea4a4838f8e2ea42fc475c486466d48020a4c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85040010"
---
# <a name="stop-a-trace-sql-server-profiler"></a>トレースの停止 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、実行中のトレースを停止する方法について説明します。  
  
 トレースを停止すると、データのキャプチャも停止します。 トレースを停止した場合、トレースを再開すると、既にキャプチャしたデータは失われます。ただし、トレース ファイルまたはトレース テーブルにキャプチャしたデータが失われることはありません。 トレースを停止した後に、キャプチャしたデータをテーブルまたはファイルに保存することは可能です。 トレースを停止しても、あらかじめ選択されているすべてのトレース プロパティは保存されます。 トレースを停止した後は、名前、イベント、列、およびフィルターを変更できます。  
  
### <a name="to-stop-a-trace"></a>トレースを停止するには  
  
1.  実行中のトレースを選択します。  
  
2.  **[ファイル]** メニューの **[トレースの停止]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
