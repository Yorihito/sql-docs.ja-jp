---
title: dm_xe_session_object_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_object_columns_TSQL
- sys.dm_xe_session_object_columns_TSQL
- dm_xe_session_object_columns
- sys.dm_xe_session_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- xe
- sys.dm_xe_session_object_columns dynamic management view
ms.assetid: e97f3307-2da6-4c54-b818-a474faec752e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 56bea991f705a9dfdbcd3189737eb3e2a51a8c63
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898566"
---
# <a name="sysdm_xe_session_object_columns-transact-sql"></a>dm_xe_session_object_columns (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  セッションにバインドされたオブジェクトの構成値を示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 sys.dm_xe_sessions.address との多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|column_name|**nvarchar(256)**|構成値の名前。 NULL 値は許可されません。|  
|column_id|**int**|列の ID。 は、オブジェクト内で一意です。 NULL 値は許可されません。|  
|column_value|**nvarchar (3072)**|列の構成値。 NULL 値が許可されます。|  
|object_type|**nvarchar(60)**|オブジェクトの古い型。 NULL 値は許可されません。 object_type は次のいずれかです。<br /><br /> イベント<br /><br /> ターゲット (target)|  
|object_name|**nvarchar(256)**|この列が所属するオブジェクトの名前。 NULL 値は許可されません。|  
|object_package_guid|**uniqueidentifier**|オブジェクトを含むパッケージの GUID。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|From|終了|リレーションシップ|  
|----------|--------|------------------|  
|dm_xe_session_object_columns。 object_name、<br /><br /> dm_xe_session_object_columns.object_package_guid|dm_xe_objects。 package_guid、<br /><br /> sys.dm_xe_objects.name|多対一|  
|dm_xe_session_object_columns。 column_name、<br /><br /> dm_xe_session_object_columns.column_id|dm_xe_object_columns。名前、<br /><br /> sys.dm_xe_object_columns.column_id|多対一|  
  
## <a name="see-also"></a>関連項目  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

