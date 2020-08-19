---
description: dbo. cdc_jobs (Transact-sql)
title: dbo. cdc_jobs (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ccb4db642eb449dfad33e5b1cd1f92aad59ddc6c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419176"
---
# <a name="dbocdc_jobs-transact-sql"></a>dbo. cdc_jobs (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  キャプチャ ジョブおよびクリーンアップ ジョブで使用される、変更データ キャプチャの構成パラメーターを格納します。 このテーブルは **msdb**に格納されます。  
  
 
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ジョブを実行するデータベースの ID。|  
|**job_type**|**nvarchar (20)**|ジョブの種類 ('capture' または 'cleanup')。|  
|**job_id**|**uniqueidentifier**|ジョブに関連付けられた一意の ID。|  
|**maxtrans**|**int**|各スキャンサイクルで処理するトランザクションの最大数。<br /><br /> **maxtrans** はキャプチャジョブでのみ有効です。|  
|**maxscans**|**int**|ログからすべての行を抽出するために実行する最大スキャン サイクル数。<br /><br /> **maxscans** は、キャプチャジョブに対してのみ有効です。|  
|**連続**|**bit**|キャプチャ ジョブを連続的に実行するか (1)、1 回だけ実行するか (0) を示すフラグ。 詳細については、「 [sys. sp_cdc_add_job &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)」を参照してください。<br /><br /> **continuous** は、キャプチャジョブに対してのみ有効です。|  
|**pollinginterval**|**bigint**|ログ スキャン サイクル間の秒数。<br /><br /> **pollinginterval** はキャプチャジョブに対してのみ有効です。|  
|**保持**|**bigint**|変更行が変更テーブルに保持される時間 (分単位)。<br /><br /> **リテンション期間** はクリーンアップジョブに対してのみ有効です。|  
|**threshold**|**bigint**|クリーンアップ時に1つのステートメントを使用して削除できる削除エントリの最大数。|  
  
## <a name="see-also"></a>参照  
 [sp_cdc_add_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sp_cdc_change_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sp_cdc_help_jobs &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sp_cdc_drop_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
