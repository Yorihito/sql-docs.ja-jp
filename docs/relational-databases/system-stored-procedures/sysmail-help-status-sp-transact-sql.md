---
title: sysmail_help_status_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_status_sp
- sysmail_help_status_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_status_sp
ms.assetid: b44277c6-81e8-4b4d-85b3-a2f04d602e7a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb00e1c2838fad01fd26d54490e1c3c29f63d397
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762646"
---
# <a name="sysmail_help_status_sp-transact-sql"></a>sysmail_help_status_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  データベースメールキューの状態を表示します。 **Sysmail_start_sp**を使用してデータベースメールキューを開始し、 **sysmail_stop_sp**データベースメールキューを停止します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_status_sp  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**状態**|**nvarchar (7)**|データベースメールの状態。 指定できる値は、[**開始**] と [**停止**] です。|  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sysadmin**固定サーバーロールのメンバーだけがこのプロシージャにアクセスできます。  
  
## <a name="examples"></a>使用例  
 次の例では、データベースメールの状態を表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_status_sp ;  
GO  
```  
  
 次に結果セットを示します。  
  
```  
Status  
-------  
STARTED  
```  
  
## <a name="see-also"></a>関連項目  
 [データベースメール外部プログラム](../../relational-databases/database-mail/database-mail-external-program.md)   
 [sysmail_start_sp &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)  
  
  
