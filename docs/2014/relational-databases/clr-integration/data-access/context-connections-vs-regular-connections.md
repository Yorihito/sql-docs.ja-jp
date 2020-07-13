---
title: 標準接続とコンテキスト接続 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: ce531129099a8f4908bdc4b29920696d4ba3c505
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970635"
---
# <a name="regular-vs-context-connections"></a>通常の接続とコンテキスト接続
  リモート サーバーに接続している場合は、常に、コンテキスト接続ではなく通常の接続を使用します。 ストアド プロシージャや関数を実行している同一サーバーに接続する必要がある場合は、ほとんどの場合、コンテキスト接続を使用します。 コンテキスト接続には、同一のトランザクション領域で実行され、再認証が不要であるなどの利点があります。  
  
 また、コンテキスト接続を使用すると、通常、パフォーマンスが向上し、リソースの使用が抑えられます。 コンテキスト接続はインプロセスのみの接続であるため、ネットワークプロトコルとトランスポート層をバイパスして Transact-sql ステートメントを送信し、結果を受け取ることによって、サーバーに直接接続できます。 認証プロセスも同様に迂回されます。 次の図に、`SqlClient` マネージド プロバイダーの主要なコンポーネントと、通常の接続を使用する場合とコンテキスト接続を使用する場合の、さまざまなコンポーネント相互の通信方法を示します。  
  
 ![コンテキストと通常の接続のコード パス](../../../database-engine/dev-guide/media/clrintdataaccess.gif "コンテキストと通常の接続のコード パス")  
  
 コンテキスト接続で使用するコード パスは、通常の接続よりも短く、関連するコンポーネントの数も少ないので、サーバーへの要求とサーバーからの結果の取得が通常の接続よりも速くなることが期待できます。 サーバーでのクエリの実行時間は、どちらの接続でも同じです。  
  
 同じサーバーに対して通常の接続を別に開く必要が生じる場合もあります。 たとえば、コンテキスト接続の使用には、[通常の接続とコンテキスト接続に関する制限](context-connections-and-regular-connections-restrictions.md)事項で説明されているような制限があります。  
  
## <a name="see-also"></a>参照  
 [コンテキスト接続](context-connection.md)  
  
  
