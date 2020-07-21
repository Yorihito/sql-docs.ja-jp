---
title: マイニングモデルのプロパティの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44313ce14beee0390f12ed0e6566502327b17795
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525038"
---
# <a name="change-the-properties-of-a-mining-model"></a>マイニング モデルのプロパティの変更
  マイニング モデルのプロパティには、モデル全体に適用されるものと個別の列に適用されるものがあります。 モデル全体に適用されるプロパティの例は、ケース データをクエリで使用可能にする必要があるかどうかを指定する `Drillthrough` プロパティと、`Description` プロパティです。 列に適用されるプロパティには、モデル内で列のデータが使用される方法を制御する `Usage` および `ModelingFlags` があります。  
  
 次のモデル プロパティには、式の作成または複雑なモデル プロパティの構成に使用できる高度なエディターがあります。 プロパティには次の機能があります。  
  
-   `Filter`[プロパティ]: [[データセットフィルター] または [モデルフィルター] ダイアログボックス](../data-set-filter-or-model-filter-dialog-box.md)を開きます。  
  
-   `AlgorithmParameters`[プロパティ]: [[マイニングモデルビュー&#41;&#40;[アルゴリズムパラメーター] ダイアログボックス](../algorithm-parameters-dialog-box-mining-models-view.md)が表示されます。  
  
 マイニング モデルのプロパティを設定する方法については、「 [マイニング モデル列](mining-model-columns.md)」を参照してください。  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>マイニング モデルのプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行のいずれかを右クリックし、 **[プロパティ]** を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>マイニング モデル列のプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング構造列とマイニング モデルが交差するグリッド内のセルを右クリックし、 **[プロパティ]** を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。  
  
    > [!NOTE]  
    >  列の使用法がに設定されている場合 `Ignore` 、列の [**プロパティ**] ウィンドウは空白になります。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](mining-model-tasks-and-how-tos.md)  
  
  
