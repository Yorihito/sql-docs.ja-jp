---
title: フラット ファイルの変換先の構成 (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc1a9102a8fa4ee834663ae839940e2db9b469e1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424979"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>[フラット ファイルの変換先の構成] (SQL Server インポートおよびエクスポート ウィザード)
  [**フラットファイル変換先の構成**] ページを使用すると、変換先フラットファイルの書式設定オプションを指定したり、結果をプレビューしてから続行することができます。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[変換元フラット ファイル]**  
 変換先ファイルの名前です。  
  
 **[行区切り記号]**  
 行の区切り記号の一覧から選択します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**{CR}{LF}**|行は、復帰と改行の組み合わせで区切られます。|  
|**リターン**|行は、復帰で区切られます。|  
|**{LF}**|行は、改行で区切られます。|  
|**セミコロン {;}**|行は、セミコロンで区切られます。|  
|**[コロン {:}]**|行は、コロンで区切られます。|  
|**傍点{,}**|行は、コンマで区切られます。|  
|**[タブ {t}]**|行は、タブで区切られます。|  
|**縦棒 (縦棒) {&#124;}**|行は、縦棒で区切られます。|  
  
 **列区切り記号**  
 列の区切り記号の一覧から選択します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**{CR}{LF}**|列は、復帰と改行の組み合わせで区切られます。|  
|**リターン**|列は、復帰で区切られます。|  
|**{LF}**|列は、改行で区切られます。|  
|**セミコロン {;}**|列は、セミコロンで区切られます。|  
|**[コロン {:}]**|列は、コロンで区切られます。|  
|**傍点{,}**|列はコンマで区切られます。|  
|**[タブ {t}]**|列は、タブで区切られます。|  
|**縦棒 (縦棒) {&#124;}**|列は、縦棒で区切られます。|  
  
 **プレビュー**  
 [データの**プレビュー** ] ダイアログボックスで、変換先のフラットファイルに対して選択した書式設定オプションの結果を表示します。  
  
 **[変換の編集]**  
 [**列マッピング**] ダイアログボックスを使用して、変換先ファイルの行の削除、行の追加、および列の構成を行います。  
  
  
