---
title: MSSQLSERVER_3271 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b255dfb092cd15865cba0a2389a50604a29404c6
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551697"
---
# <a name="mssqlserver_3271"></a>MSSQLSERVER_3271
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3271|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DMPIO_IO_ERROR|  
|メッセージ テキスト|ファイル "%ls:" %ls で回復できない I/O エラーが発生しました。|  
  
## <a name="explanation"></a>説明  
 バックアップ操作または復元操作で I/O の実行中に、オペレーティング システムからエラーが通知された場合に生じる一般エラーです。 多くの場合、バックアップ メディアがいっぱいであることが原因です。  
  
 ディスクがいっぱいであることを示す、オペレーティング システムからのテキストがエラーに含まれている場合もあります。 サード パーティ製のバックアップ ソフトウェアによるバックアップ操作や復元操作の実行中は、バックアップが失敗したことを示すメッセージも表示される場合があります。 このメッセージは次のテキストのような内容になります。  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 これは、バックアップ ソフトウェアにより、バックアップ操作または復元操作の中止が要求されたことを示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 必要に応じて、次のタスクを実行します。  
  
-   このエラーに先行して発生した、基になっているシステム エラー メッセージおよび SQL Server エラー メッセージで、障害の原因を調べます。  
  
-   バックアップ用および復元用のメディアに、十分な容量があることを確認します。  
  
-   サード パーティ製のバックアップおよび復元ソフトウェアによってエラーが発生していれば、修正します。  
  
  
