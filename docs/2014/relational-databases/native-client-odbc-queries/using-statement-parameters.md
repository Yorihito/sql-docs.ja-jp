---
title: ステートメントのパラメーターを使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 8657c439d35a539892e7f166d8a0a443a5fb759b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049725"
---
# <a name="using-statement-parameters"></a>ステートメント パラメーターの使用
  パラメーターは、ODBC アプリケーションで次の操作を可能にする SQL ステートメント内の変数です。  
  
-   テーブルの列に効果的に値を提供する。  
  
-   クエリ条件を作成する際のユーザーとの対話を強化する。  
  
-   **Text**、 **ntext**、および**Image**データおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定の C データ型を管理します。  
  
 たとえば、 **Parts**テーブルには、 **PartID**、 **Description**、および**Price**という名前の列があります。 パラメーターを使用しないで部品を追加するには、次のような SQL ステートメントを構築する必要があります。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 既知の値のセットを含む行を 1 行挿入する場合はこのステートメントでもかまいませんが、アプリケーションで複数の行を挿入する必要がある場合には不適切です。 ODBC では、アプリケーションで SQL ステートメント内のデータ値をパラメーター マーカーに置き換えることでこの問題に対処しています。 パラメーター マーカーは疑問符 (?) で表されます。 次の例では、3 つのデータ値をパラメーター マーカーに置き換えています。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 これらのパラメーター マーカーは、その後アプリケーション変数にバインドされます。 新しい行を挿入する場合は、アプリケーションでこれらの変数に値を設定し、ステートメントを実行するだけです。 ドライバーで、変数から現在値が取得され、データ ソースに送信されます。 ステートメントを複数回実行する場合は、そのステートメントを準備することで、アプリケーションの処理をより効率的にできます。  
  
 各パラメーター マーカーは、左側のパラメーターから右側のパラメーターに順番に割り当てられる序数で参照されます。 SQL ステートメントの左端のパラメーター マーカーの序数が 1、次のパラメーター マーカーの序数が 2 というように割り当てられます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [パラメーターのバインド](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;クエリの実行](executing-queries-odbc.md)  
  
  
