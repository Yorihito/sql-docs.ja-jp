---
title: MSlogreader_history (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6c4d3b61eb3031060674c248be4effd03766f1f7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889919"
---
# <a name="mslogreader_history-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSlogreader_history**テーブルには、ローカルディストリビューターに関連付けられているログリーダーエージェントの履歴行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ログリーダーエージェントの ID。|  
|**runstatus**|**int**|実行ステータスです。<br /><br /> 1 = 開始します。<br /><br /> 2 = 成功します。<br /><br /> 3 = 実行中<br /><br /> 4 = アイドル状態。<br /><br /> 5 = 再試行<br /><br /> 6 = 失敗|  
|**start_time**|**datetime**|ジョブの実行開始時刻です。|  
|**time**|**datetime**|メッセージがログに記録される時刻。|  
|**duration**|**int**|メッセージ セッションの実行時間 (秒) です。|  
|**コメント**|**nvarchar(255)**|メッセージ テキストです。|  
|**xact_seqno**|**varbinary(16)**|最後に処理されたトランザクション シーケンス番号です。|  
|**delivery_time**|**int**|最初のトランザクションが配信された時刻。|  
|**delivered_transactions**|**int**|セッションで配信されたトランザクションの合計数。|  
|**delivered_commands**|**int**|セッションで配信されたコマンドの合計数。|  
|**average_commands**|**int**|セッションで配信されたコマンドの平均数。|  
|**delivery_rate**|**float**|1秒間に配信された平均コマンド。|  
|**delivery_latency**|**int**|コマンドがパブリッシュされたデータベースに入ってからディストリビューションデータベースに入ってくるまでの待機時間。 単位はミリ秒。|  
|**error_id**|**int**|**MSrepl_error**システムテーブル内のエラーの ID。|  
|**timestamp**|**timestamp**|このテーブルのタイムスタンプ列です。|  
|**updateable_row**|**bit**|履歴行を上書きできる場合は、 **1**に設定します。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
