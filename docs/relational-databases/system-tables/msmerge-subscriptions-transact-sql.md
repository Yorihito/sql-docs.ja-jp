---
title: MSmerge_subscriptions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: eb31a5a858bb93c8ca503ba5e72687306c8750e7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889683"
---
# <a name="msmerge_subscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSmerge_subscriptions**テーブルには、サブスクライバーでマージエージェントによって提供されるサブスクリプションごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**publication_id**|**int**|パブリケーションの ID です。|  
|**subscriber_id**|**smallint**|サブスクライバーの ID です。|  
|**subscriber_db**|**sysname**|サブスクリプションデータベースの名前。|  
|**subscription_type**|**int**|サブスクリプションの種類。<br /><br /> 0 = プッシュ。<br /><br /> 1 = プル<br /><br /> 2 = 匿名。|  
|**sync_type**|**tinyint**|同期の種類。<br /><br /> 1 = 自動同期<br /><br /> 2 = 同期なし。|  
|**status**|**tinyint**|サブスクリプションの状態です。|  
|**subscription_time**|**datetime**|サブスクリプションが追加された時刻。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
