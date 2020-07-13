---
title: SQL Server 拡張イベントターゲット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 75270f5ce03de820828da65c765044a7dafdcb8f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928863"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server 拡張イベント ターゲット
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 拡張イベント ターゲットは、イベントのコンシューマーです。 ターゲットは、ファイルに書き込んだり、イベント データをメモリ バッファーに格納したり、イベント データを集計することができます。 ターゲットは、データを同期的または非同期的に処理できます。  
  
 拡張イベントの設計上、ターゲットは、セッションごとに 1 回だけイベントを受け取ります。  
  
 拡張イベント セッションで使用できる、拡張イベントに用意されたターゲットは次のとおりです。  
  
-   [イベント カウンター](../../2014/database-engine/event-counter-target.md)  
  
     拡張イベント セッション中に発生した、すべての指定されたイベントをカウントします。 完全なイベント コレクションのオーバーヘッドを追加しなくても、負荷の特性に関する情報を取得できます。 これは、同期ターゲットです。  
  
-   [イベントファイル](../../2014/database-engine/event-file-target.md)  
  
     イベント セッション出力を、メモリ バッファー全体からディスクに書き込みます。 これは、非同期ターゲットです。  
  
-   [イベント ペアリング](../../2014/database-engine/event-pairing-target.md)  
  
     ロックの取得とロックの解放など、対で発生するイベントが数多く存在します。 指定された 1 対のイベントの組み合わせが一致するかどうかを判定します。 これは、非同期ターゲットです。  
  
-   [Windows イベント トレーシング (ETW)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] イベントを、Windows オペレーティング システムまたはアプリケーション イベント データと関連付けます。 これは、同期ターゲットです。  
  
-   [ヒストグラム](../../2014/database-engine/histogram-target.md)  
  
     指定されたイベント列またはアクションに基づいて、指定されたイベントが発生する回数をカウントします。 これは、非同期ターゲットです。  
  
-   [リングバッファー](../../2014/database-engine/ring-buffer-target.md)  
  
     先入れ先出し (FIFO) 順またはイベントごとの FIFO に基づいて、イベント データをメモリに格納します。 これは、非同期ターゲットです。  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../relational-databases/extended-events/extended-events.md)   
 [拡張イベントパッケージの SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [拡張イベントセッションの SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 [SQL Server 拡張イベント エンジン](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
