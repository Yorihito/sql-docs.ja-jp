---
description: sp_cdc_stop_job (Transact-sql)
title: sp_cdc_stop_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_stop_job_TSQL
- sys.sp_cdc_stop_job
- sp_cdc_stop_job_TSQL
- sp_cdc_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_stop_job
ms.assetid: 421fc21c-c7a4-407c-8b31-359273b68c63
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d4049a54624868862faaf36b2d392836ce115c1d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489055"
---
# <a name="syssp_cdc_stop_job-transact-sql"></a>sp_cdc_stop_job (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  現在のデータベースに対して変更データ キャプチャ機能のクリーンアップ ジョブまたはキャプチャ ジョブを停止します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_stop_job [ [ @job_type = ] 'job_type' ]  
```  
  
## <a name="arguments"></a>引数  
`[ [ @job_type = ] 'job_type_' ]` 追加するジョブの種類。 *job_type* は **nvarchar (20)** で、既定値は **capture**です。 有効な入力は **キャプチャ** と **クリーンアップ**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 管理者は sys.sp_cdc_stop_job を使用してキャプチャ ジョブまたはクリーンアップ ジョブのいずれかを明示的に停止できます。  
  
## <a name="permissions"></a>アクセス許可  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、`AdventureWorks2012` データベースのクリーンアップ ジョブを停止します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_stop_job @job_type = N'capture';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [dbo. cdc_jobs &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sp_cdc_start_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)  
  
  
