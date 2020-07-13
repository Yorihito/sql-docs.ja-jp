---
title: '[作成方法の選択] (キューブウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
ms.openlocfilehash: 05bc721be827fc9f72317874d32de8815a38a412
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84538164"
---
# <a name="select-creation-method-cube-wizard"></a>[作成方法の選択] (キューブ ウィザード)
  **[作成方法の選択]** ページを使用すると、キューブの作成方法を指定できます。  
  
## <a name="options"></a>オプション  
 **[既存のテーブルの使用]**  
 データ ソース内の既存のテーブルを使用してキューブを作成する場合に選択します。 ウィザードの指示に従って、既存のテーブルに基づいてメジャー グループとディメンションを選択および定義し、新しいキューブを作成します。  
  
 **[空のキューブの作成]**  
 空のキューブを作成する場合に選択します。 このオプションは、すべてを手動で作成する場合やキューブ内のすべてのメジャー グループがリンク メジャー グループである場合に役立ちます。  
  
> [!NOTE]  
>  このオプションは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを使用している場合にのみ使用でき、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに直接接続している場合は使用できません。  
  
 **[データ ソースにテーブルを生成]**  
 キューブを作成してからそのキューブの定義に基づいてデータ ソースに新しいテーブルを生成する場合に選択します。  
  
> [!NOTE]  
>  このオプションを使用するには、基になるデータ ソースにオブジェクトを作成する権限が必要です。  
  
 このオプションを選択すると、 **[テンプレート]** オプションが有効になります。  
  
 **テンプレート**  
 キューブの作成に使用するテンプレートを選択します。 テンプレートは、特定のビジネス用途向けの定義のセットを提供します。  
  
> [!NOTE]  
>  このオプションは、 **[データ ソースにテーブルを生成]** オプションが選択された場合のみ使用できます。  
  
## <a name="see-also"></a>参照  
 [キューブオブジェクト &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md)   
 [多次元モデル内のディメンション](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
