---
title: PreConnect:Completed イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56af8e7de291c81736d2b83abf8a31a972653c8f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85052790"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed イベント クラス
  PreConnect:Completed イベント クラスは、LOGON トリガーまたはリソース ガバナー分類関数の実行が終了したことを示します。  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>PreConnect:Completed イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|いいえ|  
|SPID|`int`|このイベントを発生させるサーバー プロセスの ID。|12|はい|  
|EventSubClass|`int`|ユーザー定義の分類子関数の場合は 1。|21|はい|  
|StartTime|`datetime`|ユーザー定義の分類子関数が開始された時刻。|14|はい|  
|EndTime|`datetime`|ユーザー定義の分類子関数が開始された時刻。|15|はい|  
|Duration|`bigint`|分類子関数によって使用された時間 (マイクロ秒)。|13|はい|  
|ObjectID|`int`|ユーザー定義の分類オブジェクトの ID。|22|はい|  
|CPU|`int`|CPU 使用率 (ミリ秒単位)。|18|はい|  
|読み取り|`int`|論理読み取りの数。|16|はい|  
|書き込み|`int`|論理書き込みの数。|17|はい|  
|GroupID|`int`|分類されたワークロード グループの ID。|66|はい|  
|エラー|`int`|ユーザー定義の分類子関数が実行に失敗した場合の最後のエラー番号。|31|はい|  
|State|`int`|最後のエラーの状態。|30|はい|  
|TargetUserName|`sysname`|対応するアクティブなグループをシステムが見つけられない場合は、ユーザー定義の分類子関数の戻り値 (ワークロード グループ名)。 それ以外の場合は、この列は NULL に設定されます。|39|はい|  
|ObjectName|`nvarchar(256)`|ユーザー定義の分類子関数の 2 部構成の名前 (dbo.classifier など)。|34|はい|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../extended-events/extended-events.md)   
 [PreConnect: Starting イベントクラス](preconnect-starting-event-class.md)   
 [リソース ガバナー](../resource-governor/resource-governor.md)  
  
  
