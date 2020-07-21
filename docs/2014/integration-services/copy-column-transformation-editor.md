---
title: 列コピー変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7647d25891b37e5f09356d427072e84b45882e4c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437969"
---
# <a name="copy-column-transformation-editor"></a>列コピー変換エディター
  **[列コピー変換エディター]** ダイアログ ボックスを使用すると、コピーする列を選択して、新しい出力列に名前を割り当てることができます。  
  
 列コピー変換の詳細については、「 [列コピー変換](data-flow/transformations/copy-column-transformation.md)」をご覧ください。  
  
> [!NOTE]  
>  すべての変換元データを変換先へ単にコピーする場合、列コピー変換を使用する必要がないことがあります。 データ変換が不要な場合、状況によっては変換元を変換先に直接接続できます。 このような場合は、SQL Server インポートおよびエクスポート ウィザードを使用してパッケージを作成することをお勧めします。 パッケージでは、必要に応じて、後から機能強化や再構成が可能です。 詳細については、「 [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[使用できる入力列]**  
 チェック ボックスを使用して、コピーする列を選択します。 選択した列が入力列として下のテーブルに追加されます。  
  
 **入力列**  
 使用できる入力列の一覧からコピーする列を選択します。 選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。  
  
 **出力のエイリアス**  
 新しい出力列の別名をそれぞれ入力します。 既定では、入力列の名前の後に「 **のコピー**」と付きます。一意のわかりやすい名前を付けることもできます。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
