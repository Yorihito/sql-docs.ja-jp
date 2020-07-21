---
title: MSmerge_genhistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4c0c516062e05fe71250f8f309c12a5a3d3c89a0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889810"
---
# <a name="msmerge_genhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSmerge_genhistory**テーブルには、サブスクライバーが認識する (保有期間内の) 世代ごとに1行の情報が格納されます。 これは、交換中に共通の世代が送信されないようにし、バックアップから復元されたサブスクライバーを再同期するために使用されます。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|サブスクライバーの generation 値によって識別される変更のグローバル識別子です。|  
|**pubid**|**uniqueidentifier**|パブリケーション識別子です。|  
|**generation**|**bigint**|生成値。|  
|**art_nick**|**int**|記事のニックネーム。|  
|**ニックネーム**|**varbinary (1001)**|この generation 値を持っていることが既に認識されている他のサブスクライバーのニックネームの一覧です。 その変更を既に認識しているサブスクライバーに、generation 値を送信することを防ぐために使用します。 ニックネームの一覧のニックネームは、検索の効率を高めるために並べ替えられた順序で保持されます。 このフィールドに格納できる数よりも多くのニックネームがある場合、この最適化によるメリットは得られません。|  
|**coldate**|**datetime**|現在の generation 値がテーブルに追加された日付です。|  
|**genstatus**|**tinyint**|世代の状態を次に示します。<br /><br /> **0** = 開く。<br /><br /> **1** = Closed。<br /><br /> **2** = 閉じられ、別のサブスクライバーで発生しました。|  
|**changecount**|**int**|特定のジェネレーションに反映された変更の数|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
