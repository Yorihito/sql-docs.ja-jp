---
description: database_scoped_configurations (Transact-sql)
title: database_scoped_configurations (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||= azure-sqldw-latest
ms.openlocfilehash: 85b57b65e79dbe72c039f694f0fd3977847230b7
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "88900983"
---
# <a name="sysdatabase_scoped_configurations-transact-sql"></a>database_scoped_configurations (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2016-asdb-addw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

構成ごとに1行の値を格納します。 

|列名|データ型|説明|
|-----------------|---------------|-----------------|
|**configuration_id**|**int**|構成オプションの ID。|
|**name**|**nvarchar(60)**|構成オプションの名前。 使用可能な構成の詳細については、「 [ALTER DATABASE スコープ構成 &#40;transact-sql&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。|
|**value**|**sqlvariant**|プライマリレプリカのこの構成オプションに設定された値。|
|**value_for_secondary**|**sqlvariant**|セカンダリレプリカのこの構成オプションに設定された値。|
|**is_value_default**|**bit** |値が既定値に設定されているかどうかを指定します。|

## <a name="permissions"></a><a name="Permissions"></a> Permissions

ロール **public** のメンバーシップが必要です。

## <a name="remarks"></a>注釈

**Value_for_secondary**の値として NULL が返された場合、セカンダリがプライマリに設定されていることを意味します。
 
データベース スコープ構成設定はデータベースで継承されます。 つまり、特定のデータベースが復元されたり、アタッチされたりしたとき、既存の構成設定が残ります。

## <a name="see-also"></a>参照

[ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)
