---
title: computed_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.computed_columns_TSQL
- sys.computed_columns
- computed_columns_TSQL
- computed_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.computed_columns catalog view
ms.assetid: c962c619-e18f-4315-9251-8d9862462299
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1bbb4ef33cd640c8fe90f886f98eb966791e7003
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003061"
---
# <a name="syscomputed_columns-transact-sql"></a>computed_columns (Transact-sql)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  列が計算列である場合は、その列の行が格納され**ます。**  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<Inherited columns>**||**Computed_columns**ビューでは、すべての列が返されます、、**列、ビュー**です。 また、以下に示す追加の列も返されます。 **Computed_columns**ビューが**sys**から継承する列の詳細については、「 [sys &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)」を参照してください。 **Computed_columns**ビューでは、 **is_computed**列の値は常に1に設定されます。|  
|**カスタム**|**nvarchar(max)**|この計算列を定義する SQL テキスト。|  
|**uses_database_collation**|**bit**|1 = 列の定義は、正しい評価のために、データベースの既定の照合順序に依存します。それ以外の場合は0です。 このような依存関係によって、データベースの既定の照合順序を変更できなくなります。|  
|**is_persisted**|**bit**|計算列は保持されます。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
