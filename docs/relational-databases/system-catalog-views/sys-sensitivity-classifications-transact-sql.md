---
title: sensitivity_classifications (Transact-sql) |Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- rank
monikerRange: '>= sql-server-ver15 || = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 9962a7fbcb3b308862db7e8813ee2733155950ed
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004783"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

データベース内の分類されたアイテムごとに1行のデータを返します。

|列名|データ型|説明|
|-----------------|---------------|-----------------|  
|**class**|**int**|分類が存在する項目のクラスを識別します。 の値は常に 1 (列を表す) になります。|  
|**class_desc**|**varchar (16)**|分類が存在する項目のクラスの説明。 の値は常にになり*OBJECT_OR_COLUMN*|  
|**major_id**|**int**|All_objects に対応する、分類された列を含むテーブルの ID を表します。 object_id|  
|**minor_id**|**int**|All_columns に対応する、分類が存在する列の ID を表します。 column_id|   
|**label**|**sysname**|秘密度の分類に割り当てられたラベル (人間が判読可能)|  
|**label_id**|**sysname**|ラベルに関連付けられた ID。 Azure Information Protection (AIP) などの情報保護システムで使用できます。|  
|**information_type**|**sysname**|秘密度の分類に割り当てられた情報の種類 (人間が判読可能)|  
|**information_type_id**|**sysname**|情報の種類に関連付けられた ID。 Azure Information Protection (AIP) などの情報保護システムで使用できます。|  
|**ランク**|**int**|ランクの数値。 <br><br>NONE の場合は0<br>10 (低)<br>中20<br>高の場合は30<br>40 (重大)| 
|**rank_desc**|**sysname**|ランクのテキスト表現:  <br><br>なし、低、中、高、重大|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>コメント  

- このビューでは、データベースの分類状態を表示できます。 データベースの分類を管理したり、レポートを生成したりするために使用できます。
- 現在、データベース列の分類のみがサポートされています。
 
## <a name="examples"></a>例

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. 分類されたすべての列とそれに対応する分類の一覧表示

次の例では、データベース内の分類された各列について、テーブル名、列名、ラベル、ラベル ID、情報の種類、情報の種類の ID、順位、およびランクの説明を一覧表示するテーブルを返します。

> [!NOTE]
> Label は Azure SQL Data Warehouse のキーワードです。

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID], [Rank], [Rank_Desc]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>アクセス許可  
 [**すべての秘密度分類の表示**] アクセス許可が必要です。 
 
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  

## <a name="see-also"></a>参照  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[SQL Information Protection の概要](https://aka.ms/sqlip)
