---
title: データ変換変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e68fb1edd69e20628baaeda8802ec712da7d5117
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432619"
---
# <a name="data-conversion-transformation-editor"></a>データ変換変換エディター
  **[データ変換変換エディター]** ダイアログ ボックスを使用すると、変換対象の列や列の変換先のデータ型を選択したり、変換属性を設定したりできます。  
  
> [!NOTE]  
>  データ `FastParse` 変換の変換の出力列のプロパティは、[**データ変換変換エディター**] では使用できませんが、**詳細エディター**を使用して設定できます。 このプロパティの詳細については、「 [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)」の「データ変換の変換」を参照してください。  
  
 データ変換の変換の詳細については、「 [データ変換の変換](data-flow/transformations/data-conversion-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[使用できる入力列]**  
 変換対象の列のチェック ボックスを使用して選択します。 選択した列が入力列として下のテーブルに追加されます。  
  
 **入力列**  
 使用できる入力列の一覧から変換対象の列を選択します。 上記のチェック ボックスに、選択内容が反映されます。  
  
 **出力のエイリアス**  
 それぞれの新しい列の別名を入力します。 既定では、入力列の名前の後に "`Copy of`" が追加された別名になりますが、固有のわかりやすい名前を選択することもできます。  
  
 **[データ型]**  
 一覧から利用可能なデータ型を選択します。 詳細については、「 [Integration Services データ型](data-flow/integration-services-data-types.md)」を参照してください。  
  
 **[データ型]**  
 文字列データの列の長さを設定します。  
  
 **[精度]**  
 数値データの有効桁数を設定します。  
  
 **スケール**  
 数値データの小数点以下桁数を設定します。  
  
 **コード ページ**  
 DT_STR 型の列に適したコード ページを選択します。  
  
 **エラー出力の構成**  
 [[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [データ変換の変換を使用してデータを別のデータ型に変換する](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
