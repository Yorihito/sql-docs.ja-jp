---
title: IsTrainingCase (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e6bdfe1e3d22a2d2c4752e43df254231725fa447
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969547"
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  ケースが、指定されたデータ マイニング モデルまたはマイニング構造のトレーニング ケースとして使用されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>結果の種類  
 ケースがトレーニングデータセットの一部である場合に**true**を返します。それ以外の場合は**false**。  
  
## <a name="remarks"></a>注釈  
 データマイニングウィザードを使用してマイニング構造および関連マイニングモデルを作成する場合、既定では、ケースの30% がテストデータセットとして使用するために確保されます。 指定したデータソース内の残りのケースは、モデルのトレーニングに使用されます。 ただし、データ マイニング拡張機能 (DMX) を使用してマイニング モデルを作成する場合は、既定ですべてのデータがモデルのトレーニングに使用され、テスト セットは作成されません。 テストデータセットの作成を有効にするには、WITH 予約句のパラメーターを設定する必要があります。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> プロパティと <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> プロパティの値を表示すると、特定のデータ マイニング構造のデータがテスト セットとトレーニング セットにパーティション分割されているかどうかを確認できます。  
  
> [!NOTE]  
>  IsTrainingCase 関数または IsTestCase 関数を使用してモデル内のケースに関する詳細を返す場合は、モデルでドリルスルーを有効にする必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](https://docs.microsoft.com/analysis-services/data-mining/enable-drillthrough-for-a-mining-model)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 テストデータセットの一部であるケースを返すには、関数[IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)を使用します。  
  
## <a name="examples"></a>例  
 次の例では、「[基本的なデータマイニングチュートリアル](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」の絞り込みメール配信シナリオのクラスタリングデータマイニングモデルを使用します。 このクエリは、マイニングモデルのトレーニングに使用されたケースのみを返します。 さらに、トレーニングケースは40よりも前の顧客に制限されています。  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 データマイニングで使用されるケースをクエリする方法のその他の例については、「 [SELECT FROM &#60;model&#62;」を参照してください。DMX&#41;&#40;ケース](../dmx/select-from-model-cases-dmx.md)は[&#60;構造&#62; から選択します。ケース](../dmx/select-from-structure-cases.md)。  
  
## <a name="see-also"></a>参照  
 [トレーニングデータセットとテストデータセット](https://docs.microsoft.com/analysis-services/data-mining/training-and-testing-data-sets)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [データマイニングクエリ](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries)  
  
  
