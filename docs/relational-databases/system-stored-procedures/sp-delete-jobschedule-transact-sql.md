---
title: sp_delete_jobschedule (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobschedule
- sp_delete_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobschedule
ms.assetid: 82fbb48b-603a-4016-a7fb-1ce17fb76919
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8a74d7235b1faa80c1fe65f80717c39e7944f343
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85864274"
---
# <a name="sp_delete_jobschedule-transact-sql"></a>sp_delete_jobschedule (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  ジョブのスケジュールを削除します。  
  
 **sp_delete_jobschedule**は、旧バージョンとの互換性のためだけに用意されています。  
  
  
## <a name="remarks"></a>Remarks  
 ジョブスケジュールをジョブとは別に管理できるようになりました。 ジョブからスケジュールを削除するには、 **sp_detach_schedule**を使用します。 スケジュールを削除するには、 **sp_delete_schedule**を使用します。  
  
> **注: sp_delete_jobschedule**では、複数のジョブにアタッチされているスケジュールはサポートされていません。 既存のスクリプトが**sp_delete_jobschedule**を呼び出して、複数のジョブにアタッチされているスケジュールを削除すると、エラーが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sysadmin**固定サーバーロールのメンバーは、このストアドプロシージャを実行できます。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 **Sysadmin**ロールのメンバーは、任意のジョブスケジュールを削除できます。 **Sysadmin**ロールのメンバーでないユーザーは、自分が所有しているジョブスケジュールのみを削除できます。  
  
## <a name="see-also"></a>関連項目  
 [sp_delete_schedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [ジョブの表示または変更](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_schedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_help_jobschedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql.md)   
 [sp_update_jobschedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-jobschedule-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
