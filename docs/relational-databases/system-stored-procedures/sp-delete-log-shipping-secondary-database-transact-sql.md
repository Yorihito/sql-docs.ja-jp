---
title: sp_delete_log_shipping_secondary_database (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_secondary_database_TSQL
- sp_delete_log_shipping_secondary_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_secondary_database
ms.assetid: c71b21c0-ec04-4fbd-9735-01128b736935
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 28527dcb21243c7853439b2f8244fc1ca696b3c2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85863237"
---
# <a name="sp_delete_log_shipping_secondary_database-transact-sql"></a>sp_delete_log_shipping_secondary_database (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このストアドプロシージャは、セカンダリデータベースを削除し、ローカル履歴とリモート履歴を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database'  
```  
  
## <a name="arguments"></a>引数  
`[ @secondary_database = ] 'secondary_database'`セカンダリデータベースの名前を指定します。 *secondary_database*は**sysname**であり、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="remarks"></a>Remarks  
 **sp_delete_log_shipping_secondary_database**は、セカンダリサーバーの**master**データベースから実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
