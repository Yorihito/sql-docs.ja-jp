---
title: マイニング構造と構造列のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], column properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- properties [data mining]
ms.assetid: ce90f684-bb8c-4eca-b9e6-000794dbee16
author: minewiskan
ms.author: owend
ms.openlocfilehash: cbec968f39b8a7cf6ebebaedf55161da2d3cb172
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520618"
---
# <a name="properties-for-mining-structure-and-structure-columns"></a>マイニング構造と構造列のプロパティ
  データ マイニング デザイナーの **[マイニング構造]** タブを使用すると、マイニング構造のプロパティと、そのマイニング構造に関連付けられた列および入れ子になったテーブルのプロパティを設定または変更できます。 このタブで設定したプロパティは、その構造に関連付けられている各マイニング モデルに反映されます。  
  
> [!NOTE]  
>  マイニング構造のプロパティ値を変更した場合は、変更したのが名前や説明などのメタデータであっても、モデルの表示またはクエリを実行する前に、マイニング構造とそのモデルを再処理する必要があります。  
  
## <a name="properties-of-mining-structures-and-mining-structure-columns"></a>マイニング構造とマイニング構造列のプロパティ  
 次の表では、マイニング構造およびデータマイニングに固有のマイニング構造列のプロパティと、[**マイニング構造**] タブで表示または構成できるプロパティについて説明します。これらのプロパティを表示または構成するには、ツリービューで要素を右クリックし、[**プロパティ**] をクリックします。  
  
-   構造のプロパティを表示するには、マイニング構造の見出しをクリックします。  
  
-   列または入れ子になったテーブルのプロパティを表示するには、列名をクリックします。  
  
### <a name="properties-of-the-mining-structure"></a>マイニング構造のプロパティ  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**CacheMode**|トレーニングに使用したケースを、トレーニングの完了後にキャッシュするか破棄するかを指定します。<br /><br /> 注: `KeepTrainingCases` ドリルスルーと提示を有効にするには、このプロパティをに設定する必要があります。|  
|**Collation**|列の既定の照合順序を指定します。 照合順序を指定しない場合は、サーバーの照合順序が使用されます。|  
|**説明**|マイニング構造について説明します。 構造のデータの目的と構成について説明することをお勧めします。|  
|**ErrorConfiguration (既定)**|特別なエラー処理が行われる場合のオプションを指定します。|  
|**HoldoutMaxCases**|テスト データセットとして予約できる構造ケースの最大数を指定します。  **HoldoutMaxCases** と **HoldoutPercent**の両方に値を指定すると、それらの条件が結合されます。<br /><br /> 注: このプロパティを設定するには、を <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> に設定する必要があり `KeepTrainingCases` ます。|  
|**HoldoutPercent**|テスト データセットとして予約する構造ケースの割合を指定します。 **HoldoutMaxCases** と **HoldoutPercent**の両方に値を指定すると、それらの条件が結合されます。<br /><br /> 注: このプロパティを設定するには、を <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> に設定する必要があり `KeepTrainingCases` ます。|  
|**HoldoutSeed**|提示されたテスト セットのパーティション分割を初期化するシードを指定して、テスト データセットを確実に再作成できるようにします。<br /><br /> 注: このプロパティを設定するには、を <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> に設定する必要があり `KeepTrainingCases` ます。|  
|**ID**|マイニング構造の一意識別子を表示します。<br /><br /> マイニング構造の作成時に構造に割り当てた名前が、ID として使用されます。 その後 `Name` プロパティに新しい値を入力して名前を変更した場合、新しい名前は別名としてのみ使用され、ID は変化しません。|  
|**言語**|マイニング構造内のキャプションの言語を指定します。|  
|`Name`|マイニング構造の名前または別名を指定します。<br /><br /> Name プロパティの値を変更した場合、新しい名前はキャプションまたは別名としてのみ使用されます。マイニング構造の識別子は変化しません。|  
|**ソース**|データ ソースの名前と種類を表示します。|  
  
### <a name="properties-of-the-mining-structure-columns"></a>マイニング構造列のプロパティ  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**ClassifiedColumns**|分類列が示す列を指定します。|  
|**コンテンツ**|列のコンテンツの種類です。|  
|**説明**|列を説明します。 列の説明では、列データの派生方法やデータ マイニング用の変更について情報を提供することをお勧めします。|  
|**DiscretizationBucketCount**|離散化列のバケットの数を表示します。<br /><br /> コンテンツの種類が `Discretized` に設定されている場合にのみ有効です。<br /><br /> このプロパティは読み取り専用です。|  
|**DiscretizationMethod**|列の離散化に使用されたメソッドを表示します。<br /><br /> コンテンツの種類が `Discretized` に設定されている場合にのみ有効です。<br /><br /> このプロパティは読み取り専用です。|  
|**配布**|列のコンテンツの分布を指定します。|  
|**ID**|列の識別子を表示します。<br /><br /> 列の Name プロパティの値を変更しても、ID プロパティの値には影響を与えません。|  
|**IsKey**|列がキー列であるかどうかを示します。|  
|**[KeyColumns]**|キーであるか、属性のキーの一部である列の定義を含みます。|  
|**ModelingFlags**|アルゴリズムによって使用可能になる追加のパラメーターを設定します。|  
|`Name`|列の名前です。|  
|**NameColumn**|親要素の名前を指定する列を示します。|  
|**ソース**|列のソースを表示します。<br /><br /> リレーショナル データ ソースの場合、値は常に **(なし)** です。<br /><br /> OLAP キューブに基づく構造の場合、値は、入れ子になったテーブルのソースとして使用するスライスを定義する MDX ステートメントです。|  
|**SourceMeasureGroup**|メジャー グループのソースを表示します。<br /><br /> リレーショナル データ ソースの場合、値は常に **(なし)** です。<br /><br /> OLAP キューブに基づく構造の場合、値は、入れ子になったテーブルのソースとして使用するスライスを定義する MDX ステートメントです。|  
|**Type**|列のコンテンツのデータ型です。|  
  
 プロパティの設定または変更の詳細については、「 [マイニング構造のタスクと操作方法](mining-structure-tasks-and-how-tos.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [リレーショナルマイニング構造の作成](create-a-relational-mining-structure.md)   
 [マイニング構造列](mining-structure-columns.md)  
  
  
