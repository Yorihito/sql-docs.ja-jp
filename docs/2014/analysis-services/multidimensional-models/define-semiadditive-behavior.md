---
title: 準加法の動作を定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd433f05f17a046ed49f49ea9fbdd9f36b90a3e2
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546934"
---
# <a name="define-semiadditive-behavior"></a>準加法の動作の定義
  すべてのディメンションで一様に集計しない準加法メジャーは、多くのビジネス シナリオでよく見られます。 この問題は、一定期間の残高のスナップショットに基づくすべてのキューブで明らかです。 これらのスナップショットは、証券、口座残高、予算、人事、保険契約と保険金請求、およびその他多くのビジネス ドメインを扱うアプリケーションで見られます。  
  
 準加法の動作をキューブに追加すると、勘定科目の種類の属性の個々のメジャーまたはメンバーの集計方法を定義できます。 キューブに勘定科目ディメンションが含まれる場合は、勘定科目の種類に基づき、準加法の動作を自動的に設定できます。  
  
 準加法の動作を追加するには、キューブ デザイナーでキューブを開き、[キューブ] メニューの **[ビジネス インテリジェンスの追加]** をクリックします。 ビジネス インテリジェンス ウィザードで、 **[拡張機能の選択]** ページの **[準加法の動作の定義]** オプションを選択します。 その後、このウィザードに従って、準加法の動作のあるメジャーを識別します。  
  
 Standard Edition で使用できる LastChild を除き、準加法の動作を使用できるのは、Business Intelligence または Enterprise Edition のみです。  
  
## <a name="define-semiadditive-behavior"></a>準加法の動作の定義  
 ウィザードの **[準加法の動作の定義]** ページで、次のいずれかのオプションを選択して、準加法の定義方法を決定します。  
  
 **[準加法の動作を無効にする]**  
 準加法の動作が定義済みのキューブから準加法の動作を削除します。 メジャーが次のいずれかの種類の集計関数に設定されている場合にこのオプションを選択すると、メジャーは `SUM` にリセットされます。  
  
-   By Account  
  
-   Average of Children  
  
-   First Child  
  
-   Last Child  
  
-   Last Nonempty Child  
  
-   First Nonempty Child  
  
-   なし  
  
 このオプションでは、標準の集計関数である、 `Sum` 、 `Min` `Max` 、 `Count` 、または `Distinct``Count` のメジャーは変更されません。  
  
 **準加法メンバーを含む ' Account ' 勘定科目ディメンションが検出されました。サーバーは、勘定科目の種類ごとに指定された準加法の動作に従って、このディメンションのメンバーを集計します。**  
 Account 型のディメンションにより次元設定されたメジャー グループのすべてのメジャーが By Account 集計関数に設定され、このディメンションのメンバーは、勘定科目の種類ごとに指定されている準加法動作に従って集計されます。  
  
> [!NOTE]  
>  ウィザードで Account 型のディメンションが検出された場合は、既定でこのオプションが選択されます。  
  
 **[個別のメジャーに準加法の動作を定義する]**  
 各メジャーの準加法の動作を個別に選択します。 既定の設定は、`SUM` (完全加法) です。  
  
> [!NOTE]  
>  ウィザードで Account 型のディメンションが検出されない場合は、既定でこのオプションが選択されます。  
  
 各メジャーに対して、次の表に示した種類から準加法の機能を選択できます。  
  
|準加法関数|説明|  
|---------------------------|-----------------|  
|Average of Children|子の平均がメンバーの集計です。|  
|[ByAccount]|勘定科目の種類に対して指定された準加法を読み取ります。|  
|Count|メンバーの数が集計です。|  
|Distinct Count|一意のメンバーの数が集計です。|  
|First Child|メンバー値は時間ディメンションに従って最初の子の値として評価されます。|  
|FirstNonEmpty|メンバー値はデータを格納する時間ディメンションに従って最初の子の値として評価されます。|  
|LastChild|メンバー値は時間ディメンションに従って最後の子の値として評価されます。|  
|LastNonEmpty|メンバー値はデータを格納する時間ディメンションに従って最後の子の値として評価されます。|  
|Max|標準最大集計関数が適用されます。|  
|Min|標準最小集計関数が適用されます。|  
|なし|集計は適用されません。|  
|SUM|標準の合計関数が適用されます。|  
  
 ウィザードを完了すると、既存の準加法の動作は上書きされます。  
  
  
