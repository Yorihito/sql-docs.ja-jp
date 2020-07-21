---
title: KPI ブラウザー (キューブデザイナーの [Kpi] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b6d15cbb75f3528546c566a72f8b23323df8772
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543727"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>KPI ブラウザー (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの **[KPI]** タブの **[KPI ブラウザー]** ペインを使用すると、主要業績評価指標 (KPI) の結果を表示およびテストできます。 Kpi は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 参照する前に最初にインスタンスに配置する必要があり [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。  
  
> [!NOTE]  
>  このペインは、ブラウザー ビューでのみ表示されます。  
  
## <a name="options"></a>オプション  
 **サブキューブ グリッド**  
 サブキューブを定義し、 **[結果]** ペインに表示する KPI の結果を制限するために使用します。 このグリッドには次の列が含まれています。  
  
 **Dimension**  
 このフィルターを適用するディメンションを選択します。  
  
 **Hierarchy**  
 このフィルターを適用する階層を選択します。  
  
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
 参照する KPI 結果を制限する **[演算子]** によって評価される式を入力します。  
  
> [!NOTE]  
>  このフィールドは、動的データの入力要素であり、選択された演算子に必要なデータの型を反映して表示内容が変わります。  
  
 **結果グリッド**  
 **[フィルター グリッド]** に定義されたフィルターに基づいて、KPI の評価された値、目標、状態、および傾向を表示します。 このグリッドには次の列が含まれています。  
  
 **[構造の表示]**  
 各 KPI の **[フォルダーの表示]** または **[親 KPI]** の値に従って階層化された、キューブに含まれる KPI を表示します。  
  
 **Value**  
 KPI の値を表示します。  
  
 **Goal**  
 KPI の目標値を表示します。  
  
 **状態**  
 KPI の状態マークを表示します。  
  
 **加算**  
 KPI の傾向マークを表示します。  
  
 **Weight**  
 KPI の重み係数を表示します。  
  
 **記述**  
 KPI の説明が定義されている場合は、情報アイコンを表示します。  
  
 情報アイコン上にカーソルを配置すると、KPI を説明するツールヒントが表示されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンス上で KPI の計算中にエラーが発生した場合、このオプションは、エラーに関連付けられている情報を表示します。  
  
## <a name="see-also"></a>参照  
 [Kpi &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
