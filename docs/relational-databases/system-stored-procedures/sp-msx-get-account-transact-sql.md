---
title: sp_msx_get_account (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_get_account_TSQL
- sp_msx_get_account
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_get_account
ms.assetid: 7b478049-e2d0-4bac-865a-b97fd1d8dfbc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ddb3d983b37bdad5db334073fe168b518aaee77a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893463"
---
# <a name="sp_msx_get_account-transact-sql"></a>sp_msx_get_account (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  対象サーバーがマスターサーバーへのログインに使用する資格情報に関する情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_msx_get_account  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の結果セットを返します。  
  
|列名|種類|説明|  
|-----------------|----------|-----------------|  
|msx_connection|**int**|マスターサーバーの接続番号。|  
|msx_credential_id|**int**|このマスターサーバー接続に使用される資格情報の ID。|  
|msx_credential_name|**sysname**|このマスターサーバー接続に使用される資格情報の名前。|  
|msx_login_name|**nvarchar (4000)**|資格情報に関する Windows ユーザーのドメイン名とユーザー名。|  
  
## <a name="remarks"></a>Remarks  
 ターゲット サーバーに対して指定された資格情報がない場合、空の結果セットを返します。 資格情報を設定するには、sp_msx_set_account を使用します。  
  
## <a name="permissions"></a>アクセス許可  
 sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、このターゲット サーバーがマスター サーバーにログインする場合に使用する資格情報を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_get_account ;  
GO  
```  
  
 結果セットの例を次に示します。  
  
 `msx_connection msx_credential_id msx_credential_name  msx_login_name`  
  
 `-------------- ----------------- -------------------- ------------------------------`  
  
 `1              65538             MsxAccount           AdventureWorks2012\MsxAccount`  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;のストアドプロシージャの SQL Server エージェント](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;の資格情報の作成](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_set_account &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-msx-set-account-transact-sql.md)  
  
  
