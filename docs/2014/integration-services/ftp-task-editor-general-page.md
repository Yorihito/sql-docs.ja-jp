---
title: FTP タスクエディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 381493758306e3f7c638f46f7c331f0e6cc3e83f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425319"
---
# <a name="ftp-task-editor-general-page"></a>[FTP タスク エディター] ([全般] ページ)
  **[FTP タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、タスクの通信先の FTP サーバーに接続する FTP 接続マネージャーを指定できます。 また、FTP タスクの名前と説明を入力することもできます。  
  
 このタスクの詳細については、「 [FTP タスク](control-flow/ftp-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[FtpConnection]**  
 既存の FTP 接続マネージャーを選択するか、をクリックして \<**New connection...**> 接続マネージャーを作成します。  
  
> [!IMPORTANT]  
>  FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 **関連トピック**: [FTP 接続マネージャー](connection-manager/ftp-connection-manager.md)、 [FTP 接続マネージャー エディター](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
 **[StopOnFailure]**  
 FTP 操作が失敗した場合に FTP タスクを終了するかどうかを示します。  
  
 **名前**  
 FTP タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **説明**  
 FTP タスクの説明を入力します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [FTP タスクエディター &#40;ファイル転送ページ&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
