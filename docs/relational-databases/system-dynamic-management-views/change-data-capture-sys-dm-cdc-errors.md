---
description: 変更データキャプチャ-sys. dm_cdc_errors
title: dm_cdc_errors (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cdc_errors_TSQL
- dm_cdc_errors
- sys.dm_cdc_errors
- sys.dm_cdc_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cdc_errors dynamic management view
- change data capture [SQL Server], error reporting
ms.assetid: 898f2d76-9e63-45ef-94da-8034e86004ab
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b34623ac9b7732faff5b1f29e6a154dddf79dd78
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482045"
---
# <a name="change-data-capture---sysdm_cdc_errors"></a>変更データキャプチャ-sys. dm_cdc_errors
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  変更データキャプチャのログスキャンセッション中に発生したエラーごとに1行のデータを返します。  
 
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|セッションの ID。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
|**phase_number**|**int**|エラー発生時のセッションのフェーズを示す数値です。 各フェーズの説明については、「 [sys. dm_cdc_log_scan_sessions &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)」を参照してください。|  
|**entry_time**|**datetime**|エラーがログに記録された日付と時刻。 この値は、SQL エラーログのタイムスタンプに相当します。|  
|**error_number**|**int**|エラーメッセージの ID。|  
|**error_severity**|**int**|メッセージの重大度レベル (1 ~ 25)。|  
|**error_state**|**int**|エラーの状態番号。|  
|**error_message**|**nvarchar(1024)**|エラーのメッセージテキスト。|  
|**start_lsn**|**nvarchar (23)**|エラー発生時に処理されていた行の開始 LSN 値です。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
|**begin_lsn**|**nvarchar (23)**|エラーが発生したときに処理されていたトランザクションの開始 LSN 値。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
|**sequence_value**|**nvarchar (23)**|エラー発生時に処理されていた行の LSN 値です。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
  
## <a name="remarks"></a>解説  
 **dm_cdc_errors** には、前の32セッションのエラー情報が含まれています。  
  
## <a name="permissions"></a>アクセス許可  
 **Dm_cdc_errors**動的管理ビューに対してクエリを実行するには、VIEW DATABASE STATE 権限が必要です。 動的管理ビューに対する権限の詳細については、「 [transact-sql&#41;&#40;の動的管理ビューおよび関数 ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [dm_cdc_log_scan_sessions &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)   
 [dm_repl_traninfo &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-repl-traninfo-transact-sql.md)  
  
  

