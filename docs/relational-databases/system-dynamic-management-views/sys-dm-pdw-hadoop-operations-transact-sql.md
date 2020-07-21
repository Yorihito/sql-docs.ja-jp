---
title: dm_pdw_hadoop_operations (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6378ddd4b0604fabe81d669d272b59207781fdf8
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197075"
---
# <a name="sysdm_pdw_hadoop_operations-transact-sql"></a>dm_pdw_hadoop_operations (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  外部 Hadoop テーブルに対するクエリの実行の一部として Hadoop にプッシュされるマップ削減ジョブごとに1行の情報を格納 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] します。 各 map reduce ジョブは、クエリ内のいずれかの述語を表します。 これは、Hadoop の外部テーブルに対するクエリに対して述語のプッシュダウンが有効になっている場合にのみ使用されます。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この外部 Hadoop 操作の ID。|[Transact-sql&#41;&#40;dm_pdw_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)の ID と同じです。|  
|step_index|**int**|この Hadoop 操作を参照するクエリステップのインデックス。|[Dm_pdw_request_steps &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)の step_index と同じです。|  
|operation_type|**nvarchar(255)**|外部操作の種類を記述します。|' 外部 Hadoop 操作 '|  
|operation_name|**nvarchar (4000)**|マップ削減ジョブのジョブ ID。 これは、ジョブを送信した後に Hadoop によって返され [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ます。||  
|map_progress|**float**|マップジョブによってこれまでに使用された入力データの割合。|、0、および100の間の浮動小数点数。|  
|reduce_progress|**int**|完了した reduce ジョブの割合。|、0、および100の間の浮動小数点数。|  
  
## <a name="see-also"></a>関連項目  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
