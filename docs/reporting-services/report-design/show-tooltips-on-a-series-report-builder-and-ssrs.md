---
title: 系列へのツールヒントの表示 (レポート ビルダー) | Microsoft Docs
description: レポート ビルダーで関連情報を表示するため、グラフの系列上の各データにツールヒントを追加する方法について説明します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f89c94b8a9b457ff312acfd97d84632f037de82a
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681481"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a>系列へのツールヒントの表示 (レポート ビルダーおよび SSRS)
  グラフの系列上の各データ ポイントにツールヒントを追加すると、データ ポイントに関連する情報 (グループ名、データ ポイントの値、系列の合計に対するデータ ポイントの比率など) が表示されます。 この情報は、表示されている改ページ調整されたレポートのデータ ポイントにユーザーがマウス カーソルを合わせたときに表示されます。  
  
 計算系列にはツールヒントを追加できません。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-tooltip-on-each-data-point"></a>各データ ポイントにツールヒントを指定するには  
  
1.  系列を右クリックするか、 **[値]** 領域のフィールドを右クリックし、 **[系列のプロパティ]** をクリックします。  
  
2.  **[系列データ]** をクリックし、 **ToolTip** プロパティに文字列または式を入力します。 グラフ固有のキーワードを使用して、グラフ上の別の要素を表すことができます。 詳細については、「 [グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)をクリックします。  
  
## <a name="see-also"></a>参照  
 [グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [レポートへのドリルスルー アクションの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
