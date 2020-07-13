---
title: Visual FoxPro データベースから Microsoft Excel にデータをインポートする |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bfd86233e5a0a406febcb30bf7a4fae595e53d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287672"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Visual FoxPro データベースから Microsoft Excel へのデータのインポート
データソースを定義している場合は、Visual FoxPro データを Microsoft Excel ワークシートにインポートできます。 Visual FoxPro データソースの作成の詳細については、「 [Microsoft Excel からの Visual Foxpro データソースへのアクセス](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md)」を参照してください。  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Microsoft Excel ワークシートに Visual FoxPro データをインポートするには  
  
1.  Microsoft Excel スプレッドシートを開きます。  
  
2.  [データ] メニューの [外部データの取り込み] をクリックします。 Microsoft Query が開きます。  
  
3.  [データソースの選択] ダイアログボックスで、Visual FoxPro データソースを選択し、[使用] をクリックします。  
  
4.  データソースによってアクセスされるデータベースにテーブルが含まれている場合は、[テーブルの追加] ダイアログボックスでテーブルを選択します。 Microsoft Query では、クエリデザイナーの上半分に追加したテーブルが表示されます。  
  
    > [!NOTE]  
    >  このダイアログボックスでは所有者がサポートされていないため、所有者の一覧は使用できません。 ドライバーがデータソース内の複数のデータベースをサポートしていないため、データベースの一覧を使用できません。  
  
5.  テーブルからデザイナーの下半分にクエリをドラッグして、クエリのフィールドを選択します。  
  
6.  Microsoft Query を終了します。 選択したデータは、Microsoft Excel スプレッドシートにインポートされます。
