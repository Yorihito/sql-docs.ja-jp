---
description: sys.sysログイン (Transact-sql)
title: sys.sysログイン (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
author: rothja
ms.author: jroth
ms.openlocfilehash: 075e78b9f8e765cad359a136e643f594ce6638b3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475113"
---
# <a name="syssyslogins-transact-sql"></a>sys.sysログイン (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  ログインアカウントごとに1行のレコードを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から[現在のバージョン](https://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**sid**|**varbinary (85)**|セキュリティ識別子。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|ログインが追加された日付です。|  
|**updatedate**|**datetime**|ログインが更新された日付です。|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**timelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|ユーザーのログイン名。|  
|**dbname**|**sysname**|接続が確立されたときのユーザーの既定のデータベース名。|  
|**password**|**nvarchar(128)**|NULL を返します。|  
|**language**|**sysname**|ユーザーの既定の言語です。|  
|**denylogin**|**int**|1 = ログインは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザーまたはグループであり、アクセスは拒否されました。|  
|**hasaccess**|**int**|1 = ログインには、サーバーへのアクセスが許可されています。|  
|**isntname**|**int**|1 = ログインは Windows ユーザーまたはグループです。<br /><br /> 0 = ログインは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインです。|  
|**isntgroup**|**int**|1 = ログインは Windows グループです。|  
|**isntuser**|**int**|1 = ログインは Windows ユーザーです。|  
|**sysadmin**|**int**|1 = ログインは、 **sysadmin** サーバーロールのメンバーです。|  
|**securityadmin**|**int**|1 = ログインは、 **securityadmin** サーバーロールのメンバーです。|  
|**serveradmin**|**int**|1 = ログインは、 **serveradmin** 固定サーバーロールのメンバーです。|  
|**setupadmin**|**int**|1 = ログインは、 **setupadmin** 固定サーバーロールのメンバーです。|  
|**processadmin**|**int**|1 = ログインは、 **processadmin** 固定サーバーロールのメンバーです。|  
|**diskadmin**|**int**|1 = ログインは、 **diskadmin** 固定サーバーロールのメンバーです。|  
|**dbcreator**|**int**|1 = ログインは **dbcreator** 固定サーバーロールのメンバーです。|  
|**bulkadmin**|**int**|1 = ログインは、 **bulkadmin** 固定サーバーロールのメンバーです。|  
|**ログイン**|**nvarchar(128)**|ユーザーのログイン名。 これは旧バージョンとの互換性のために用意されています。|  
  
## <a name="see-also"></a>参照  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
