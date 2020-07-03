---
title: sp_delete_schedule (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8fe6f851ffb3ab15781d5a2ffbbcaca3bf15829f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85862800"
---
# <a name="sp_delete_schedule-transact-sql"></a>sp_delete_schedule (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  スケジュールを削除します。  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_schedule { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @force_delete = ] force_delete  
```  
  
## <a name="arguments"></a>引数  
`[ @schedule_id = ] schedule_id`削除するスケジュールの識別番号を指定します。 *schedule_id*は**int**,、既定値は NULL です。  
  
> **注:***Schedule_id*または*schedule_name*のいずれかを指定する必要がありますが、両方を指定することはできません。  
  
`[ @schedule_name = ] 'schedule_name'`削除するスケジュールの名前を指定します。 *schedule_name*は**sysname**,、既定値は NULL です。  
  
> **注:***Schedule_id*または*schedule_name*のいずれかを指定する必要がありますが、両方を指定することはできません。  
  
`[ @force_delete = ] force_delete`スケジュールがジョブにアタッチされている場合にプロシージャを失敗させるかどうかを指定します。 *Force_delete*はビット,、既定値は**0**です。 *Force_delete*が**0**の場合、スケジュールがジョブにアタッチされていると、ストアドプロシージャは失敗します。 *Force_delete*が**1**の場合、スケジュールがジョブにアタッチされているかどうかに関係なく、スケジュールは削除されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 既定では、スケジュールがジョブに関連付けられている場合、スケジュールを削除することはできません。 ジョブに関連付けられているスケジュールを削除するには、 *force_delete*に値**1**を指定します。 スケジュールを削除しても、現在実行中のジョブは停止されません。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sysadmin**固定サーバーロールのメンバーは、このストアドプロシージャを実行できます。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 ジョブの所有者はスケジュールにジョブをアタッチし、スケジュールの所有者でなくてもジョブをスケジュールからデタッチできることに注意してください。 ただし、呼び出し元がスケジュールの所有者でない限り、デタッチによってジョブが存在しない場合、スケジュールを削除することはできません。  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 **Sysadmin**ロールのメンバーだけが、別のユーザーが所有するジョブスケジュールを削除できます。  
  
## <a name="examples"></a>例  
  
### <a name="a-deleting-a-schedule"></a>A. スケジュールを削除する  
 次の例では、スケジュールを削除し `NightlyJobs` ます。 スケジュールがジョブにアタッチされている場合、この例ではスケジュールは削除されません。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="b-deleting-a-schedule-attached-to-a-job"></a>B: ジョブに関連付けられているスケジュールを削除する  
 次の例では、スケジュールがジョブに関連付けられているかどうかに関係なく、スケジュール `RunOnce` を削除します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = 'RunOnce',  
    @force_delete = 1;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [ジョブの実装](../../ssms/agent/implement-jobs.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
  
