---
title: SQL Server プロファイラーを使用して Analysis Services を監視する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543734"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>SQL Server Profiler を使用した Analysis Services の監視
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、バッチまたはトランザクションの開始などのエンジン プロセス イベントが追跡され、そのようなイベントに関するデータがキャプチャされて、サーバーおよびデータベースの利用状況 (ユーザー クエリ、ログインの利用状況など) を監視できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはファイルにキャプチャして、後で分析できます。また、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同じインスタンスまたは別のインスタンスでキャプチャしたイベントを再生して、何が起こったかを正確に確認することもできます。 イベントはリアルタイムまたはステップごとに再生できます。 また、同じコンピューター上のパフォーマンス カウンターと共にトレース イベントを実行すると非常に役立ちます。 このプロファイラーでは、これらの 2 つを時間に基づいて関連付けることができます。また、1 つの時間軸で同時に表示できます。 パフォーマンス カウンターは集計を表示しますが、トレース イベントではより詳細なデータが得られます。 トレースを作成および実行する方法については、「 [再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)」を参照してください。  
  
 このトピックでは、次の内容について紹介します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[SQL Server Profiler による Analysis Services の監視の概要](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを監視する方法について説明します。|  
|[再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して再生用トレースを作成するための要件について説明します。|  
|[Analysis Services トレース イベント](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のイベント クラスについて説明します。 これらのイベント クラスは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって生成されるアクションにマップされ、トレースの再生に使用されます。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスの監視](monitor-an-analysis-services-instance.md)  
  
  
