---
title: SQL Server 変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857e0a9ae7b8432703cdf1b89617ab6a61b18f5a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437639"
---
# <a name="sql-server-destination-custom-properties"></a>SQL Server 変換先のカスタム プロパティ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントに共通するプロパティの両方があります。  
  
 次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|AlwaysUseDefaultCodePage|Boolean|DefaultCodePage プロパティ値を強制的に使用します。 このプロパティの既定値は `False` です。|  
|BulkInsertCheckConstraints|Boolean|一括挿入で制約をチェックするかどうかを指定する値。 このプロパティの既定値は `True` です。|  
|BulkInsertFireTriggers|Boolean|一括挿入でテーブル上のトリガーを起動するかどうかを指定する値。 このプロパティの既定値は `False` です。|  
|BulkInsertFirstRow|Integer|挿入する最初の行を指定する値。 このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。|  
|BulkInsertKeepIdentity|Boolean|ID 列に値を挿入できるかどうかを指定する値。 このプロパティの既定値は `False` です。|  
|BulkInsertKeepNulls|Boolean|一括挿入で NULL 値を保持するかどうかを指定する値。 このプロパティの既定値は `False` です。|  
|BulkInsertLastRow|Integer|挿入する最後の行を指定する値。 このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。|  
|BulkInsertMaxErrors|Integer|一括挿入を停止する前に許容するエラー数を指定する値。 このプロパティの既定値は、 **-1**です。これは、割り当てられた値がないことを示します。|  
|BulkInsertOrder|String|並べ替え列の名前。 各列は、昇順または降順で並べ替えることができます。 並べ替え列を複数使用する場合、列の名前はコンマで区切ります。|  
|BulkInsertTableName|String|データのコピー先となる、データベース内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはビュー。|  
|BulkInsertTablock|Boolean|一括挿入中にテーブルをロックするかどうかを指定する値。 このプロパティの既定値は `True` です。|  
|DefaultCodePage|Integer|コード ページに関する情報をデータ ソースから取得できない場合に使用するコード ページ。|  
|MaxInsertCommitSize|Integer|バッチに挿入する行の最大数を示す値。 値がゼロのときは、単一のバッチにすべての行が挿入されます。|  
|タイムアウト|Integer|挿入できるデータがない場合、終了前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先が待機する秒数を指定する値。 値を 0 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先はタイムアウトしません。このプロパティの既定値は 30 です。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [SQL Server 変換先](sql-server-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
