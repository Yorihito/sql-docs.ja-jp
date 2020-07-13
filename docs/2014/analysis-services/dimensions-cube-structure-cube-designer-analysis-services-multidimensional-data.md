---
title: '[ディメンション] (キューブデザイナーの [キューブ構造] タブ) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.dimensionspane.f1
ms.assetid: 37eb7525-b423-4df5-9e62-9f4680d47b9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb68b07a4e14e16a8df5acde7bea986733564253
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528558"
---
# <a name="dimensions-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a>[ディメンション] (キューブ デザイナーの [キューブ構造] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの **[キューブ構造]** タブの **[ディメンション]** ペインを使用すると、階層と属性を含むキューブ ディメンションを表示したり、編集したりできます。  
  
## <a name="options"></a>オプション  
 **Hierarchies (階層)**  
 クリックすると、使用できるキューブ ディメンションと、それに関連付けられているキューブの階層が表示されます。  
  
 キューブディメンションを展開し、 **[ \<dimension> 編集**] をクリックしてディメンションデザイナーを表示し、キューブディメンションの基になるデータベースディメンションを編集します。 ディメンション デザイナーの詳細については、「[ディメンション デザイナー &#40;Analysis Services - 多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **属性**  
 クリックすると、使用できるキューブ ディメンションと、それに関連付けられているキューブの属性が表示されます。  
  
 キューブディメンションを展開し、 **[ \<dimension> 編集**] をクリックしてディメンションデザイナーを表示し、キューブディメンションの基になるデータベースディメンションを編集します。 ディメンション デザイナーの詳細については、「[ディメンション デザイナー &#40;Analysis Services - 多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
## <a name="context-menu"></a>コンテキスト メニュー  
 次に、 **[ディメンション]** ペインを右クリックして表示されるショートカット メニューで、使用可能なオプションを示します。  
  
 **[キューブ ディメンションの追加]**  
 クリックすると、 **[キューブ ディメンションの追加]** ダイアログ ボックスを表示して、キューブ内の既存のデータベース ディメンションまたは新しいデータベース ディメンションへの参照を追加できます。 **[キューブ ディメンションの追加]** ダイアログ ボックスの詳細については、「[[キューブ ディメンションの追加] ダイアログ ボックス (Analysis Services - 多次元データ)](add-cube-dimension-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
> [!NOTE]  
>  このオプションは、ディメンションが選択されている場合にのみ表示されます。  
  
 **[ディメンションの編集]**  
 クリックすると、ディメンション デザイナーが表示され、キューブ ディメンションの基となるデータベース ディメンションを編集できます。 ディメンション デザイナーの詳細については、「[ディメンション デザイナー &#40;Analysis Services - 多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **名前の変更**  
 クリックすると、キューブに選択されているキューブ ディメンションの名前を変更できます。  
  
> [!NOTE]  
>  **[ディメンション]** ペインでキューブ ディメンションの名前を変更しても、キューブ ディメンションが基づいているデータベース ディメンションの名前は変更されません。  
  
> [!NOTE]  
>  このオプションは、ディメンションが選択されている場合にのみ表示されます。  
  
 **削除**  
 クリックすると、選択されているキューブ ディメンションをキューブから削除できます。  
  
> [!NOTE]  
>  **[ディメンション]** ペインからキューブ ディメンションを削除しても、キューブ ディメンションが基づいているデータベース ディメンションは削除されません。  
  
> [!NOTE]  
>  このオプションは、ディメンションが選択されている場合にのみ表示されます。  
  
 **[上へ移動]**  
 クリックすると、選択したキューブ データベースを 1 つ上に移動します。  
  
> [!NOTE]  
>  このオプションは、ディメンションが選択されている場合にのみ表示されます。  
  
 **[上へ移動]**  
 クリックすると、選択したキューブ データベース属性を 1 つ下に移動します。  
  
> [!NOTE]  
>  このオプションは、ディメンションが選択されている場合にのみ表示されます。  
  
 **[新しいリンク オブジェクト]**  
 クリックすると、 **リンク オブジェクト ウィザード** を表示して、他のキューブのメジャー グループおよびディメンションをリンクしたり、選択したキューブにアクション、KPI、および計算をインポートしたりできます。 **リンク オブジェクト ウィザード**の詳細については、「 [リンク オブジェクト ウィザードの F1 ヘルプ](linked-object-wizard-f1-help.md)」を参照してください。  
  
> [!NOTE]  
>  このオプションは、ディメンションが選択されている場合にのみ表示されます。  
  
 **プロパティ**  
 クリックすると **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィンドウが開き、選択したキューブ ディメンション、キューブ階層、またはキューブ属性のプロパティが表示されます。  
  
## <a name="see-also"></a>参照  
 [ツールバー &#40;キューブデザイナーの [キューブ構造] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md)   
 [メジャー &#40;キューブデザイナーの [キューブ構造] タブ&#41; &#40;Analysis Services-多次元データ&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md)   
 [キューブデザイナーの [キューブ構造] タブの [データソースビュー &#40;&#41; &#40;Analysis Services-多次元データ&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md)   
 [キューブ構造 &#40;キューブデザイナーの&#41; &#40;Analysis Services-多次元データ&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md)  
  
  
