---
title: データの手動処理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a861225414ec5bb63f77a0c4ce6c76a9c58c153d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541844"
---
# <a name="manually-process-data-ssas-tabular"></a>データの手動処理 (SSAS テーブル)
  このトピックでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のワークスペースのデータを手動で処理する方法について説明します。  
  
 外部データを使用するテーブル モデルを作成すると、[処理] コマンドを使用してデータを手動で更新できます。 1 つのテーブル、モデル内のすべてのテーブル、または 1 つ以上のパーティションを処理できます。 データを処理するときには、データの再計算も必要になることがあります。  データの処理とは、外部ソースから最新のデータを取得することです。 再計算とは、データを使用する数式の結果を更新することです。  
  
 このトピックのセクション:  
  
-   [データの手動処理](#bkmk_mahually_process)  
  
-   [データ処理の進行状況](#bkmk_data_process_progress)  
  
##  <a name="manually-process-data"></a><a name="bkmk_mahually_process"></a>データを手動で処理する  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a>モデル内の 1 つまたはすべてのテーブルのデータを処理するには  
  
1.  モデル デザイナーで、処理するテーブルをクリックします。  
  
2.  **[モデル]** メニュー、 **[処理]** の順にクリックし、 **[処理]** または **[すべて処理]** をクリックします。  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a>同じ接続を使用するすべてのテーブルのデータを処理するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[既存の接続]** をクリックします。  
  
2.  **[既存の接続]** ダイアログ ボックスで接続を選択し、 **[処理]** をクリックします。  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a>1 つ以上のパーティションのデータを処理するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[処理]** をポイントして **[パーティションの処理]** をクリックします。  
  
2.  **[パーティションの処理]** ダイアログ ボックスの **[モード]** で、次のプロセス モードのいずれかを選択します。  
  
    |モード|説明|  
    |----------|-----------------|  
    |**既定の処理**|パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。 空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築されます。|  
    |**完全処理**|パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。 既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。 この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。|  
    |**データの処理**|階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。|  
    |**消去の処理**|パーティションからすべてのデータを削除します。|  
    |**追加の処理**|パーティションを新しいデータで増分更新します。|  
  
3.  [パーティション] リストで処理するパーティションを選択し、 **[OK]** をクリックします。  
  
##  <a name="data-process-progress"></a><a name="bkmk_data_process_progress"></a>データ処理の進行状況  
 **[データ処理の進行状況]** ダイアログ ボックスを使用すると、外部ソースからモデルにインポートしたデータの処理を監視できます。 このダイアログ ボックスにアクセスするには、 **[モデル]** メニューの **[パーティションの処理]**、 **[テーブルの処理]** 、または **[すべて処理]** をクリックします。  
  
 **状態**  
 処理の操作が正常に行われたかどうかを示します。  
  
 **詳細**  
 インポートされたテーブルやビュー、インポートされた行の数を一覧表示し、問題のあるレポートへのリンクを示します。  
  
 **[更新の停止]**  
 処理の操作を停止します。 このオプションは、操作に時間がかかりすぎる場合や、エラーが多すぎる場合に有効です。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;データを処理する](process-data-ssas-tabular.md)   
 [データの処理のトラブルシューティング &#40;SSAS テーブル&#41;](troubleshoot-process-data-ssas-tabular.md)  
  
  
