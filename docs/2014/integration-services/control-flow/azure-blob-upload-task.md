---
title: Azure BLOB のアップロード タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ca15c5a77a2694293981121f4e5927be8ec0e1c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433939"
---
# <a name="azure-blob-upload-task"></a>Azure BLOB のアップロード タスク
  Azure BLOB のアップロード タスクを使うと、SSIS パッケージで Azure BLOB ストレージにファイルをアップロードできます。   
**Azure BLOB のアップロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックし、次の **[Azure Blob Upload Task Editor (Azure BLOB アップロード タスク エディター)]** ダイアログ ボックスを表示します。  
  
 次の表で、このダイアログ ボックスの各フィールドを説明します。  
  
|||  
|-|-|  
|**フィールド**|**説明**|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。|  
|BlobContainer|アップロードしたファイルを BLOB として保持する BLOB コンテナーの名前を指定します。|  
|BlobDirectory|アップロードしたファイルをブロック BLOB として格納する BLOB ディレクトリを指定します。 BLOB ディレクトリは仮想階層構造です。 BLOB が既に存在する場合は置き換えられます。|  
|LocalDirectory|アップロードするファイルを含むローカル ディレクトリを指定します。|  
|FileName|指定された名前のパターンを使用したファイルを選択するための名前フィルターを指定します。 例: MySheet*.xls\* には、MySheet001.xls や MySheetABC.xlsx などのファイルが含まれます。|  
|TimeRangeFrom/TimeRangeTo|時間範囲フィルターを指定します。 **TimeRangeFrom** から **TimeRangeTo** までの間に変更されたファイルが含まれます。|  
  
  
