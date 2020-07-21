---
title: フラット ファイル ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2aed708179edf8359f7943afa6b00edc0a997e51
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432159"
---
# <a name="flat-file-source"></a>フラット ファイル ソース
  フラット ファイル ソースは、テキスト ファイルからデータを読み取ります。 テキスト ファイルには、Delimited 形式、FixedWidth 形式、または Mixed 形式を使用できます。  
  
-   Delimited 形式では、列区切り記号と行区切り記号を使用して、列と行が定義されます。  
  
-   FixedWidth 形式では、幅を使用して列と行を定義します。 またこの形式には、フィールドを幅いっぱいまで埋めるための文字も含まれています。  
  
-   RaggedRight 形式では、幅を使用して最終列以外のすべての列を定義します。最終列は、行区切り記号で区切られます。  
  
 フラット ファイル ソースは、次の方法で構成できます。  
  
-   変換出力に列を追加します。列には、フラット ファイル ソースによるデータの抽出元となるテキスト ファイルの名前が含まれています。  
  
-   フラット ファイル ソースで、列にある長さ 0 の文字列を NULL 値として解釈するかどうかを指定します。  
  
    > [!NOTE]  
    >  長さ 0 の文字列を NULL として解釈するには、フラット ファイル ソースで使用するフラット ファイル接続マネージャーを、Delimited 形式を使用するように構成する必要があります。 フラット ファイル接続マネージャーで FixedWidth 形式または RaggedRight 形式が使用される場合、空白文字で構成されるデータを NULL 値として解釈できません。  
  
 フラット ファイル ソースの出力にある出力列には、FastParse プロパティが含まれています。 FastParse は、列が、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に用意されているロケール非依存型の高速な解析ルーチンを使用するか、ロケール依存型の標準的な解析ルーチンを使用するかを示します。 詳細については、「 [Fast Parse](../fast-parse.md) 」および「 [Standard Parse](../standard-parse.md)」を参照してください。  
  
 出力列には、UseBinaryFormat プロパティも含まれます。 このプロパティを使用して、パック 10 進形式を使用するデータなど、バイナリ データのサポートをファイルに実装します。 既定では、UseBinaryFormat はに設定されて `false` います。 バイナリ形式を使用する場合は、UseBinaryFormat をに設定 `true` し、出力列のデータ型をに設定し `DT_BYTES` ます。 この設定を行った場合、フラット ファイル ソースはデータ変換をスキップし、データを出力列にそのまま渡します。 この場合は、派生列変換またはデータ変換などの変換を使用して `DT_BYTES` データを別のデータ型にキャストするか、スクリプト変換でカスタム スクリプトを記述してデータを解釈できます。 また、カスタム データ フロー コンポーネントを記述してデータを解釈することもできます。 キャストできるデータ型の詳細については `DT_BYTES` 、「 [CAST &#40;SSIS 式&#41;](../expressions/cast-ssis-expression.md)」を参照してください。  
  
 フラット ファイル ソースは、フラット ファイル接続マネージャーを使用してテキスト ファイルにアクセスします。 フラット ファイル接続マネージャーでプロパティを設定することにより、ファイルおよびファイルの各列に関する情報を提供して、フラット ファイル ソースで、テキスト ファイルのデータをどのように処理するかを指定できます。 たとえば、ファイルの列と行を区切る文字や、各列のデータ型や長さを指定できます。 詳しくは、「 [フラット ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」をご覧ください。  
  
 この変換は、1 つの出力と 1 つのエラー出力をとります。  
  
## <a name="configuration-of-the-flat-file-source"></a>フラット ファイル ソースの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[フラット ファイル ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [フラット ファイル ソース エディター &#40;[接続マネージャー] ページ&#41;](../flat-file-source-editor-connection-manager-page.md)  
  
-   [フラット ファイル ソース エディター ([列] ページ)](../flat-file-source-editor-columns-page.md)  
  
-   [フラット ファイル ソース エディター ([エラー出力] ページ)](../flat-file-source-editor-error-output-page.md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../common-properties.md)  
  
-   [フラット ファイルのカスタム プロパティ](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 データ フロー コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [フラットファイル変換先](flat-file-destination.md)   
 [データ フロー](data-flow.md)  
  
  
