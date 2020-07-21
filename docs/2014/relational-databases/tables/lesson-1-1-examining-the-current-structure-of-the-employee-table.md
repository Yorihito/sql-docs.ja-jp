---
title: Employee テーブルの現在の構造の確認 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a5561d0f2398a0a1adc12ae30a7cd7527fdd5d45
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068103"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a>Employee テーブルの現在の構造の確認
   サンプル [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースには、**HumanResources** スキーマに含まれる **Employee** テーブルがあります。 元のテーブルを変更しないように、この手順では、 **Employee** テーブルのコピーを作成して **EmployeeDemo**という名前を付けます。 例を単純にするために、元のテーブルから 5 列だけをコピーします。 次に、 **Humanresources.employee demo**テーブルに対してクエリを実行し、データ型を使用せずにテーブルでデータがどのように構造化されているかを確認します `hierarchyid` 。  
  
### <a name="to-copy-the-employee-table"></a>Employee テーブルをコピーするには  
  
1.  クエリ エディターのウィンドウで、次のコードを実行し、 **Employee** テーブルから新しいテーブルの **EmployeeDemo**にテーブル構造とデータをコピーします。  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>EmployeeDemo テーブルの構造とデータを確認するには  
  
-   この新しい **EmployeeDemo** テーブルは、新しい構造に移行可能な、既存のデータベースの一般的なテーブルを表しています。 クエリ エディター ウィンドウで次のコードを実行すると、テーブルで自己結合を使用して従業員と管理者のリレーションシップを示しているようすを確認できます。  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     結果は合計 290 行にわたります。  
  
 `ORDER BY` 句を使用していることによって、出力では、各管理レベルの直属の部下がまとめて表示されていることに注意してください。 たとえば、 **MgrID** 3 (roberto0) の 7 人の直属の部下がすべて左右に並べて表示されています。 実際に **MgrID** 3 に直属するすべての人をグループ化することは、不可能ではありませんが、かなり難しくなります。  
  
 次の作業では、`hierarchyid` データ型を使用して新しいテーブルを作成し、この新しいテーブルにデータを移動します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [既存の階層データを使用したテーブルの設定](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
