---
title: 評価レポート (Sql server による) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c28fb4cf5d110e01b156fc6ce985b2cb2fb7bfe1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67910680"
---
# <a name="assessment-report-accesstosql"></a>評価レポート (Sql server による)
[評価レポート] ウィンドウには、データベースオブジェクトを構文に[!INCLUDE[tsql](../../includes/tsql-md.md)]変換した結果が表示されます。また、移行プロジェクトの複雑さとコストを見積もるのにも役立ちます。  
  
評価レポートを作成するには、ソースメタデータエクスプローラーで変換するオブジェクトを選択し、[**データベース**] を右クリックして、[**レポートの作成**] を選択します。 スキーマを変換した後に、このレポートを自動的に表示することもできます。 ただし、レポート名は変換レポートになります。 詳細については、「[プロジェクトの設定 (GUI) (SSMA Common)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)」を参照してください。  
  
## <a name="options"></a>オプション  
**エクスプローラー ペイン**  
評価レポートのオブジェクトの階層が含まれます。 [フォルダー] を展開して、個々のオブジェクトとサブコンポーネントを表示します。 カテゴリまたはオブジェクトをクリックすると、そのカテゴリまたはオブジェクトの変換統計が詳細ウィンドウに表示されます。  
  
**詳細ウィンドウ**  
選択したオブジェクトの変換の統計情報またはエラーと警告メッセージを表示します。 たとえば、[テーブル] フォルダーを選択した場合、[詳細] ペインには、変換された外部キー、インデックス、主キー、およびテーブルの数が表示されます。  
  
**メッセージ ペイン (Messages pane)**  
評価レポートの作成時に生成されたエラー、警告、および情報メッセージを表示します。 メッセージは数値でグループ化されます。  
  
メッセージの詳細を表示するには、[**エラー**]、[**警告**]、または [**メッセージ**] をクリックし、メッセージを展開します。 SSMA には、このエラーが発生したオブジェクトの一覧が表示されます。 オブジェクトをクリックすると、そのオブジェクトのすべての変換の詳細が表示されます。  
  
## <a name="see-also"></a>参照  
[ユーザーインターフェイスリファレンス (アクセス)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
