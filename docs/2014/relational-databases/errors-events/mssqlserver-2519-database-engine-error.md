---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 641f91922fc23be368265ab22a326624f2ec7d89
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034320"
---
# <a name="mssqlserver_2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2519|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_NO_EXPRESSION_EVALUATOR|  
|メッセージ テキスト|内部の式エバリュエーターを初期化できなかったため、オブジェクト ID O_ID (オブジェクト "O_NAME") の計算列とユーザー定義型を確認できません。|  
  
## <a name="explanation"></a>説明  
 この情報メッセージは、クエリ プロセッサが、計算列と CLR (common language runtime) ユーザー定義型を評価するための内部オブジェクトを DBCC に提供できなかったことを示しています。 つまり、計算列および CLR ユーザー定義型の正当性チェックが行われなかったり、DBCC でインデックスとベース テーブルの整合性をチェックする際に計算列が使用されないことを意味します。  
  
## <a name="user-action"></a>ユーザーの操作  
 なし  
  
## <a name="see-also"></a>参照  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
