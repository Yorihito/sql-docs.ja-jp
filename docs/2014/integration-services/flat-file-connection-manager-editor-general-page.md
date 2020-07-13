---
title: '[フラットファイル接続マネージャーエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 82181fad0220ad73804c23d7ebce2fbe6994d820
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425659"
---
# <a name="flat-file-connection-manager-editor-general-page"></a>[フラット ファイル接続マネージャー エディター] ([全般] ページ)
  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、ファイルおよびデータ形式を選択できます。 フラット ファイル接続により、パッケージをテキスト ファイルに接続できるようになります。  
  
 フラット ファイル接続マネージャーの詳細については、「 [Flat File Connection Manager](connection-manager/file-connection-manager.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **接続マネージャー名**  
 ワークフローにおけるフラット ファイル接続の一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **説明**  
 接続の説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。  
  
 **[ファイル名]**  
 フラット ファイル接続で使用するパスおよびファイル名を入力します。  
  
 **参照**  
 フラット ファイル接続で使用するファイル名を探します。  
  
 **ロケール**  
 ロケールを指定して、順序付けおよび日時の形式に関する言語固有の情報を提供します。  
  
 **Unicode**  
 Unicode を使用するかどうかを示します。 Unicode を使用する場合は、コード ページを指定できません。  
  
 **コード ページ**  
 非 Unicode テキストのコード ページを指定します。  
  
 **Format**  
 区切り記号形式、固定幅形式、または幅合わせしない形式をファイルで使用するかどうかを示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|区切り記号|列は、 **[列]** ページで指定した区切り記号で区切られます。|  
|固定幅ファイル|列は固定幅を持ちます。|  
|[幅合わせしない]|幅合わせしない形式のファイルとは、最後の列を除くすべての列が固定幅のファイルです。 最後の列は、行区切り記号で区切られます。|  
  
 **テキスト修飾子**  
 使用するテキスト修飾子を指定します。 たとえば、テキスト フィールドを引用符で囲むことを指定できます。  
  
> [!NOTE]  
>  テキスト修飾子を選択した後で、 **[なし]** オプションを再度選択することはできません。 テキスト修飾子の選択を解除するには、「 **なし** 」と入力します。  
  
 **[ヘッダー行区切り記号]**  
 ヘッダー行の区切り記号の一覧から選択するか、区切り記号テキストを入力します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**{CR}{LF}**|ヘッダー行は、復帰と改行の組み合わせで区切られます。|  
|**リターン**|ヘッダー行は、復帰で区切られます。|  
|**{LF}**|ヘッダー行は、改行で区切られます。|  
|**セミコロン {;}**|ヘッダー行は、セミコロンで区切られます。|  
|**[コロン {:}]**|ヘッダー行は、コロンで区切られます。|  
|**傍点{,}**|ヘッダー行は、コンマで区切られます。|  
|**[タブ {t}]**|ヘッダー行は、タブで区切られます。|  
|**縦棒 (縦棒) {&#124;}**|ヘッダー行は、縦棒で区切られます。|  
  
 **[スキップするヘッダー行数]**  
 必要に応じて、スキップするヘッダー行数または初期データ行数を指定します。  
  
 **[先頭データ行を列名として使用する]**  
 先頭データ行を列名として使用するか、ここに列名を指定するかを示します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[フラットファイル接続マネージャーエディター &#40;列] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)   
 [[フラットファイル接続マネージャーエディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)   
 [[フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
