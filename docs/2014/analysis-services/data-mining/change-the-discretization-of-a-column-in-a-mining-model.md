---
title: マイニングモデルの列の分離を変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f5dfbc1ab2481afc1b4f4b152c7748f9ac5a03a
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525068"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>マイニング モデルでの列の分離の変更
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]値を自動的に分離します。つまり、特定のシナリオでは、数値列にデータをビン分割します。 たとえば、データに連続する数値データが含まれている場合にデシジョン ツリー モデルを作成すると、データの分布に応じて、連続するデータの各列が自動的にビン分割されます。 データの分離方法を制御するには、モデルでのデータの使用方法を制御するマイニング構造列のプロパティを変更する必要があります。  
  
 マイニング モデルでプロパティを設定する方法については、 [「マイニング モデル列」](mining-model-columns.md)を参照してください。  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>マイニング モデル列のプロパティを表示するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行を右クリックし、 **[プロパティ]** を選択します。  
  
     マイニング モデル全体に関連付けられているプロパティが、 **[プロパティ]** ウィンドウに表示されます。  
  
2.  画面の左側にある **[構造]** 列で、分離の対象となる連続する数値データを含んだ列をクリックします。  
  
     クリックした列に関連付けられているプロパティのみが **[プロパティ]** ウィンドウに表示されるようになります。  
  
### <a name="to-change-the-discretization-method"></a>分離メソッドを変更するには  
  
1.  [**マイニングプロパティ**] ウィンドウで、[**コンテンツ**] の横にあるテキストボックスをクリックし、 `Discretized` ドロップダウンリストからを選択します。  
  
     マイニング モデル全体に関連付けられているプロパティが、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> プロパティと <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティが有効になりました。  
  
2.  [**プロパティ**] ウィンドウで、の横にあるテキストボックスをクリックし、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 、、 `Automatic` またはのいずれかの値を選択します `EqualAreas` `Cluster` 。  
  
    > [!NOTE]  
    >  列の使用法がに設定されている場合 `Ignore` 、列の [**プロパティ**] ウィンドウは空白になります。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
3.  データ マイニング デザイナーの **[プロパティ]** ウィンドウで、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> の横にあるテキスト ボックスをクリックし、数値を入力します。  
  
    > [!NOTE]  
    >  これらのプロパティを変更した場合は、新しい設定を使用するモデルと共に構造を再処理する必要があります。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](mining-model-tasks-and-how-tos.md)  
  
  
