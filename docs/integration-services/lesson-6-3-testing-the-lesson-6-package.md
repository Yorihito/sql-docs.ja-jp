---
title: 手順 3:レッスン 6 のパッケージをテストする | Microsoft Docs
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0c50372c199d80dc0e6d3d7e3326918011f8a28
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "71283063"
---
# <a name="lesson-6-3-test-the-lesson-6-package"></a>レッスン 6-3:レッスン 6 のパッケージをテストする

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


パッケージを実行すると、**VarFolderName** パラメーターから **Directory** プロパティの値が取得されます。  
  
パッケージによって **Directory** プロパティが更新されることを確認するには、パッケージを実行します。 新しいディレクトリにはサンプル データ ファイルを 3 つコピーしたため、データ フローは 3 回実行されます。
  
## <a name="check-the-package-layout"></a>パッケージ レイアウトを確認する  
パッケージをテストする前に、レッスン 6 の制御フローとデータ フローが次の図にあるオブジェクトと同様であることを確認します。   
  
**制御フロー**  
  
![制御フロー](../integration-services/media/task4lesson2control.gif "制御フロー")  
  
**データ フロー**  
  
![データ フロー](../integration-services/media/task5lesson5data.gif "Data Flow")  
  
## <a name="test-the-lesson-6-package"></a>レッスン 6 のパッケージをテストする  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]** を選択します。  
  
2.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** を選択します。  
  
## <a name="go-to-next-task"></a>次のタスクに進む
[手順 4:レッスン 6 のパッケージを配置する](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
