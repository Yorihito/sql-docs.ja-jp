---
title: イベントカウンターターゲット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f540f39176ec638cdc9236b315e306ecebfdcb1b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933073"
---
# <a name="event-counter-target"></a>イベント カウンター ターゲット
  イベント カウンター ターゲットは、拡張イベント セッション中に発生したすべてのイベントをカウントします。 イベント カウンター ターゲットを使用すると、完全なイベント コレクションのオーバーヘッドを追加することなく負荷の特性に関する情報を取得できます。 このターゲットには、カスタマイズ可能なパラメーターはありません。  
  
## <a name="adding-the-target-to-a-session"></a>セッションへのターゲットの追加  
 イベント カウンター ターゲットを拡張イベント セッションに追加するには、イベント セッションの作成時または変更時に次のステートメントを含める必要があります。  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a>ターゲット出力の確認  
 イベント カウンター ターゲットの出力を確認するには、 *session_name* をイベント セッションの名前に置き換えて、次のクエリを使用します。  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 次の例は、イベント カウンター ターゲットの出力形式を示しています。  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a>参照  
 [拡張イベントターゲットの SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [dm_xe_session_targets &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [Transact-sql&#41;&#40;のイベントセッションの作成](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
