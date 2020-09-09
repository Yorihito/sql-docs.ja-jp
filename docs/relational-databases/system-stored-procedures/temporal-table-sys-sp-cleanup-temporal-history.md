---
description: sp_cleanup_temporal_history (Transact-sql)
title: sys. sp_cleanup_temporal_history |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3b47fd6b0ee5a06ae1ce585f583a699a530e350b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545795"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sp_cleanup_temporal_history (Transact-sql)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

1つのトランザクション内で構成された HISTORY_RETENTION 期間に一致する、テンポラル履歴テーブルからすべての行を削除します。

## <a name="syntax"></a>構文

```
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```

## <a name="arguments"></a>引数

*\@table_name*

保持クリーンアップが呼び出されるテンポラルテーブルの名前。

*schema_name*

現在のテンポラルテーブルが属しているスキーマの名前

*row_count_var* [出力]

削除された行の数を返す出力パラメーター。 履歴テーブルにクラスター化列ストアインデックスがある場合、このパラメーターは常に0を返します。

## <a name="remarks"></a>解説

このストアドプロシージャは、有限の保有期間が指定されているテンポラルテーブルでのみ使用できます。
このストアドプロシージャは、履歴テーブルからすべての期限切れの行を直ちに消去する必要がある場合にのみ使用してください。 同じトランザクション内で対象となるすべての行が削除されるため、データベースログと i/o サブシステムに大きな影響を与える可能性があります。

一般に通常のワークロードとデータベースへの影響を最小限に抑えて、期限切れの行を削除するクリーンアップの内部バックグラウンドタスクに依存することをお勧めします。

## <a name="permissions"></a>アクセス許可

Db_owner のアクセス許可が必要です。

## <a name="example"></a>例

```sql
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="next-steps"></a>次のステップ

[テンポラルテーブルのリテンション期間ポリシー](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
