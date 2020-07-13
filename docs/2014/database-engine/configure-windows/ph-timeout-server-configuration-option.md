---
title: PH timeout サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935126"
---
# <a name="ph-timeout-server-configuration-option"></a>PH timeout サーバー構成オプション
  PH timeout オプションは、フルテキスト プロトコル ハンドラーが、データベースへの接続をタイムアウトするまで待機する時間を秒単位で指定します。既定値は 60 秒です。 一時的なネットワークの問題により接続試行がタイムアウトする場合は、ph timeout 値を大きくします。  
  
 フルテキスト プロトコル ハンドラーは、フィルター デーモン ホストでホストされ、フルテキスト インデックスの作成対象データを SQL Server からフェッチする場合に使用されます。 フルテキスト検索コンポーネントの詳細については、「 [フルテキスト検索](../../relational-databases/search/full-text-search.md)」を参照してください。  
  
 データ行をフェッチすると、指定した時間内にプロトコル ハンドラーが SQL Server に接続できない場合、その行に対するタイムアウト エラーが報告されます。 その行のフェッチは、後でフルテキストの Gatherer により再試行されます。 フルテキストの Gatherer の詳細については、「 [フルテキスト インデックスの作成](../../relational-databases/indexes/indexes.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
