---
title: クエリとフィルター (キューブデザイナーの [ブラウザー] タブ) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: aa501e2a5b23f32fbd10d244788b1e6e938e938b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539734"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>クエリとフィルター (キューブ デザイナーの [ブラウザー] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの **[ブラウザー]** タブのこの領域には、参照目的で使用するデータやクエリに使用するデータをキューブから簡単に選択できるクエリ/フィルター領域があります。 キューブ オブジェクトは必要に応じていくつでも追加でき、その結果をデータ領域で確認することができます。また、"Excel で分析" を使用して結果をレポートにエクスポートすることにより、エンド ユーザーから見たデータの体裁を視覚的に確認することができます。  
  
> [!WARNING]  
>  この領域でデータを扱うときは、 **[ブラウザー]** が既定でグラフィカル デザイン モードになります。 ただし、 **[デザイン モード]** 切り替えボタンをクリックすると、MDX を使用して直接クエリを編集できます。 この場合、ディメンションに対するフィルターをデザインするためのペインは非表示になります。 フィルターを追加する必要がある場合は、再度グラフィカル デザイン モードに切り替えてください。  
  
 既定では、クエリの実行時、データ ソースへの接続には、 **[権限借用情報]** ページで指定された資格情報ではなく、現在のユーザーの資格情報が使用されます。 ただし、 **ツール バー** の **[ユーザーの変更]** をクリックすることによって、クエリまたはレポートのユーザー コンテキストを変更することもできます。  
  
## <a name="options"></a>オプション  
 **Dimension**  
 サブキューブをスライスするディメンションを選択します。  
  
 **Hierarchy**  
 サブキューブをスライスする階層を選択します。  
  
 **Operator**  
 **[フィルター式]** の式を、選択した階層に適用する方法を定義する演算子を選択します。 次の表では、使用可能な演算子について説明しています。  
  
|値|説明|  
|-----------|-----------------|  
|**Equal**|結果は **[フィルター式]** で定義された設定に制限されます。|  
|**等しくない**|結果は **[フィルター式]** で定義された設定によって除外されたメンバーに制限されます。|  
|**In**|結果は **[フィルター式]** で選択された名前付きセットに制限されます。|  
|**含まれない**|結果は **[フィルター式]** で選択された名前付きセットによって除外されたメンバーに制限されます。|  
|**内容**|結果は **[フィルター式]** にある文字列をメンバー名に含むメンバーに制限されます。|  
|**で始まる**|結果は **[フィルター式]** にある文字列で始まるメンバー名を持つメンバーに制限されます。|  
|**[範囲 (包含)]**|結果は **[フィルター式]** で選択された範囲に制限されます。|  
|**[範囲 (排他)]**|結果は **[フィルター式]** で選択された範囲によって除外されたメンバーに制限されます。|  
|**MDX (MDX)**|結果は **[フィルター式]** で設定された多次元式 (MDX) に制限されます。|  
  
 **[フィルター式]**  
 **[演算子]** によって評価される式を入力します。この式により、参照される結果が制限されます。  
  
> [!NOTE]  
>  このフィールドは、動的データの入力要素であり、選択された演算子に必要なデータの型を反映して表示内容が変わります。  
  
## <a name="see-also"></a>参照  
 [キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [ブラウザー &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [ツールバー &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [[Excel で分析] &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [[メタデータ &#40;ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
