---
title: インデントの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1fe1685bf1f56b2b2e7a0feac31ba3a601b0e51b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041044"
---
# <a name="adding-indentation"></a>インデントの追加
  クエリ エディターでは、大規模なコードのセクションに一括してインデントを適用できるほか、インデント幅を変更できます。  
  
## <a name="indenting-code"></a>コードへのインデントの適用  
  
#### <a name="to-indent-multiple-lines-of-code"></a>複数行のコードにインデントを適用するには  
  
1.  ツール バーの **[新しいクエリ]** をクリックします。  
  
2.  ここでは、 **Person**スキーマの **Person**テーブルから、 **BusinessEntityID** 、FirstName、 **MiddleName** 、 **LastName** の各列を選択する新しいクエリを作成します。 次のようにコードを入力します。各列を別々の行に入力してください。  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  `BusinessEntityID` から `LastName`までのテキストをすべて選択します。  
  
4.  **[SQL エディター]** ツール バーの **[インデント]** をクリックし、すべての行に一括してインデントを適用します。  
  
#### <a name="to-change-the-default-indentation"></a>既定のインデントを変更するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[テキスト エディター]**、 **[すべての言語]** の順に展開し、 **[タブ]** をクリックして、適切なインデント幅を設定します。 インデント幅とタブのサイズを変更できるほか、タブをスペースに変換するかどうかも指定できます。  
  
     ![[タブ] オプション ([オプション] ダイアログ ボックス)](media/tabsdialog.gif "[タブ] オプション ([オプション] ダイアログ ボックス)")  
  
3.  **[OK]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [クエリ エディターの最大化](lesson-2-3-maximizing-query-editor.md)  
  
  
