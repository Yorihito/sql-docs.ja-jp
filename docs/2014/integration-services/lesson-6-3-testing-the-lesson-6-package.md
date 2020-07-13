---
title: '手順 3: レッスン 6 のパッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 37c4bbccc7c63ab2c2fdc6f64793281cf4c88349
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440329"
---
# <a name="step-3-testing-the-lesson-6-package"></a>手順 3:レッスン 6 のパッケージのコピー
  パッケージを実行すると、VarFolderName パラメーターから Directory プロパティの値が取得されます。  
  
 パッケージの実行時に、Directory プロパティが新しい値に更新されているかどうかを確認するには、パッケージを実行してみます。 3 つのサンプル データ ファイルのみが新しいディレクトリにコピーされるため、データ フローは 3 回だけ実行されます。元のフォルダーの 14 ファイルには反復処理は実行されません。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
 パッケージをテストする前に、次の図に示すオブジェクトがレッスン 6 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 5 の制御フローと同じである必要があります。 データ フローはレッスン 5 のデータ フローと同じである必要があります。  
  
 **制御フロー**  
  
 ![制御フロー](../../2014/tutorials/media/task3lesson6control.jpg "制御フロー")  
  
 **データ フロー**  
  
 ![データ フロー](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>レッスン 6 のチュートリアル パッケージをテストするには  
  
1.  [デバッグ] メニューの [デバッグの開始] をクリックします。  
  
2.  パッケージの実行が完了したら、[デバッグ] メニューの [デバッグの停止] をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 4:レッスン 6 のパッケージの展開](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
