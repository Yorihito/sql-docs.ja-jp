---
title: external_library_files (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2020
ms.prod: sql
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: a7f6038f9929d1220d3fb272ce3bdd9aa726a551
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173583"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE [SQL Server 2017 SQL MI](../../includes/applies-to-version/sqlserver2017-asdbmi.md)]

外部ライブラリを構成するファイルごとに1行の情報を一覧表示します。

|列名 |データ型 |説明|
|------|------|-----|
|external_library_id | INT |外部ライブラリオブジェクトの ID。 |
|コンテンツ |varbinary(max) |外部ライブラリファイルの成果物のコンテンツ。 |
|platform |tinyint |SQL Server がインストールされているホストプラットフォームの ID。 |
|platform_desc | nvarchar(60) |ホストプラットフォームの名前。 有効な値は ' WINDOWS '、' LINUX ' です。 |

### <a name="see-also"></a>こちらもご覧ください  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)  
