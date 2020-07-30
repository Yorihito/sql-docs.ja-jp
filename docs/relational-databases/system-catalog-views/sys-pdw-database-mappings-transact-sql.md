---
title: pdw_database_mappings (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 013a6bcbba5e7647db1bec04204f8e8fec710c16
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396095"
---
# <a name="syspdw_database_mappings-transact-sql"></a>pdw_database_mappings (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  **Database_id**のデータベースを、コンピューティングノードで使用される物理名にマップし、システム上のデータベース所有者の**プリンシパル id**を提供します。 Sys. **pdw_database_mappings**を pdw_nodes_pdw_physical_databases**に結合し**ます**sys.pdw_nodes_pdw_physical_databases**。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar (36)**|計算ノード上のデータベースの物理名。<br /><br /> このビューのキーは**physical_name**と**database_id**によって形成されます。||  
|database_id|**int**|データベースのオブジェクト ID。 「[データベース &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)」を参照してください。<br /><br /> このビューのキーは**physical_name**と**database_id**によって形成されます。||  
  
## <a name="examples-sspdw"></a>例: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、pdw_database_mappings を他のシステムテーブルに結合して、データベースがどのようにマップされているかを示します。  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [pdw_index_mappings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [pdw_table_mappings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [pdw_nodes_pdw_physical_databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

