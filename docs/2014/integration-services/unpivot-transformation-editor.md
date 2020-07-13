---
title: ピボット解除変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45aeb428f0905b7bf96900b6d592ff11963d8f4d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420319"
---
# <a name="unpivot-transformation-editor"></a>[ピボット解除変換エディター]
  **[ピボット解除変換エディター]** ダイアログ ボックスを使用すると、行でピボットする列を選択したり、データ列および新しいピボット値出力列を指定したりできます。  
  
> [!NOTE]  
>   このトピックでは、「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) 」に示されているピボット解除の例に基づいて、オプションの使用方法を説明します。  
  
 ピボット解除変換の詳細については、「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[使用できる入力列]**  
 チェック ボックスを使用して、行でピボットする列を指定します。  
  
 **名前**  
 使用できる入力列の名前を表示します。  
  
 **[パススルー]**  
 ピボット解除された出力に列を含めるかどうかを示します。  
  
 **入力列**  
 各行に対して使用できる入力列の一覧から選択します。 選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。  
  
 「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、入力列として、 **Ham**, **Soda**, **Milk**, **Beer**、および **Chips** の各列があります。  
  
 **変換先列**  
 データ列の名前を指定します。  
  
 「 [ピボット解除変換](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、変換先列は数量 (**Qty**) 列です。  
  
 **[ピボット キー値]**  
 ピボット値の名前を指定します。 既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。  
  
 このプロパティの値は、プロパティ式を使用して指定することができます。  
  
 「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、ピボット値は、 **[ピボット キー値の列名]** オプションで指定された新しい Product 列のテキスト値 **Ham**, **Soda**, **Milk**, **Beer**、および **Chips**として表示されます。  
  
 **[ピボット キー値の列名]**  
 ピボット値列の名前を指定します。 既定では [ピボット キー値] になりますが、わかりやすい一意な名前を選択することもできます。  
  
 「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、ピボット キー値列の名前は **Product** です。これは、 **Product** 、 **Product**, **Product**, **Product**, **Product**の列のピボット解除が行われる新しい **Product** 列を示しています。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [ピボット変換](data-flow/transformations/pivot-transformation.md)  
  
  
