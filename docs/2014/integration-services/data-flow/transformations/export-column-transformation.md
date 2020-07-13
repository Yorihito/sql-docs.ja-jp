---
title: 列エクスポート変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2914c6a23a326f4d312c2784eaad2b84fdad0b0e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430649"
---
# <a name="export-column-transformation"></a>列エクスポート変換
  列エクスポート変換は、データ フローのデータを読み取り、そのデータをファイルに挿入します。 たとえば、データ フローに、各製品の写真などの製品情報が含まれる場合、列エクスポート変換を使用して、その画像をファイルに保存できます。  
  
## <a name="append-and-truncate-options"></a>追加オプションと切り捨てオプション  
 次の表では、追加オプションと切り捨てオプションが結果に与える影響について説明します。  
  
|Append|Truncate|ファイルが存在するか|[結果]|  
|------------|--------------|-----------------|-------------|  
|False|False|いいえ|新しいファイルが作成され、そのファイルにデータが書き込まれます。|  
|True|False|いいえ|新しいファイルが作成され、そのファイルにデータが書き込まれます。|  
|False|True|いいえ|新しいファイルが作成され、そのファイルにデータが書き込まれます。|  
|True|True|いいえ|デザイン時の検証に失敗します。 両方のプロパティに `true` を設定するのは無効です。|  
|False|False|はい|実行時エラーが発生します。 ファイルは存在しますが、そのファイルに書き込めません。|  
|False|True|はい|ファイルが削除されて再作成され、データが書き込まれます。|  
|True|False|はい|ファイルが開かれ、そのファイルの終わりにデータが書き込まれます。|  
|True|True|はい|デザイン時の検証に失敗します。 両方のプロパティに `true` を設定するのは無効です。|  
  
## <a name="configuration-of-the-export-column-transformation"></a>列エクスポート変換の構成  
 列エクスポート変換は、次の方法で構成できます。  
  
-   データ列と、データの書き込み先のファイルのパスが含まれる列を指定します。  
  
-   データ挿入の操作の際に既存のファイルを追加するか、または切り捨てるかを指定します。  
  
-   バイト順マーク (BOM) をファイルに書き込むかどうかを指定します。  
  
    > [!NOTE]  
    >  BOM は、データが既存のファイルに追加されず、DT_NTEXT データ型の場合にのみ書き込まれます。  
  
 この変換では、ファイル名が含まれる入力列と、データが含まれる入力列の組を使用します。 データセットの各行では、異なるファイルを指定できます。 この変換により行が処理されると、データは指定したファイルに挿入されます。 実行時に既存のファイルがない場合、変換によりファイルが作成され、そのファイルにデータが書き込まれます。 書き込まれるデータは、DT_TEXT、DT_NTEXT、または DT_IMAGE データ型である必要があります。 詳細については、「 [Integration Services Data Types](../integration-services-data-types.md)」を参照してください。  
  
 この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[列エクスポート変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「[[列エクスポート変換エディター] ([列] ページ)](../../export-column-transformation-editor-columns-page.md)」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
