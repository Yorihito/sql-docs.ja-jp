---
description: fn_hadr_distributed_ag_database_replica (Transact-sql)
title: fn_hadr_distributed_ag_database_replica (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_database_replica
- sys.fn_hadr_distributed_ag_database_replica_TSQL
- fn_hadr_distributed_ag_database_replica
- fn_hadr_distributed_ag_database_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_database_replica
ms.assetid: 0e6202a1-e872-4f53-99d7-c16b6f712efc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f54cfdf987474435b452421620246b6432892a36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419506"
---
# <a name="sysfn_hadr_distributed_ag_database_replica-transact-sql"></a>fn_hadr_distributed_ag_database_replica (Transact-sql)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  分散型可用性グループ内のデータベースを、ローカル可用性グループ内のデータベースにマップするために使用します。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_hadr_distributed_ag_database_replica( lag_Id, database_id )  
```  
  
## <a name="arguments"></a>引数  
 '*lag_Id*'  
 分散型可用性グループの識別子を示します。 *lag_Id* 型は **uniqueidentifier**です。  
  
 '*database_id*'  
 分散型可用性グループ内のデータベースの識別子を示します。 *database_id* 型は **uniqueidentifier**です。  
  
## <a name="tables-returned"></a>返されるテーブル  
 次の情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**group_database_id**|**uniqueidentifier**|ローカル可用性グループ内のデータベースの ID。|  
  
## <a name="examples"></a>例  
  
### <a name="using-sysfn_hadr_distributed_ag_database_replica"></a>Fn_hadr_distributed_ag_database_replica の使用  
 次の例では、分散型可用性グループのデータベース ID を渡します。 このメソッドは、ローカル可用性グループに関連付けられているデータベース ID を含むテーブルを返します。  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @databaseId uniqueidentifier = '3FFA882A-C4C3-5B9E-A203-8F44BD9659F7'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_database_replica(@lagId, @databaseId)  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Always On 可用性グループの関数 &#40;Transact-sql&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [分散型可用性グループ &#40;Always On 可用性グループ&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
