---
title: dbo.sysproxylogin (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 67e119b52b2dcb741ce1c63b343970e3152ccee5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890415"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  各 SQL Server エージェント プロキシ アカウントに関連付けられている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログインを記録します。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシ アカウントの ID。 この値は、 **sysproxies**テーブルの**proxy_id**列に対応しています。|  
|**sid**|**varbinary (85)**|SQL Server ログイン用の Microsoft Windows *security_identifier* 。|  
|**principal_id**|**int**|指定されたサブシステムステップでプロキシアカウントを使用する権限を持つユーザーまたはグループの ID。|  
|**flags**|**int**|ログインの種類:<br /><br /> **0** = Windows ユーザーまたはグループ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン。<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定システムロール<br /><br /> **2**  = **msdb**データベースロール|  
  
## <a name="remarks"></a>Remarks  
 このテーブルにアクセスできるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [dbo.sysプロキシ &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
