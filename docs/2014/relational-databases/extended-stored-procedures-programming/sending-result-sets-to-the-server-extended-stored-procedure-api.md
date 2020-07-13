---
title: 結果セットのサーバーへの送信 (拡張ストアドプロシージャ API) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050861"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>結果セットのサーバーへの送信 (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 結果セットをに送信する場合 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、拡張ストアドプロシージャは次のように適切な API を呼び出す必要があります。  
  
-   **Srv_sendmsg**関数は、すべての行 (存在する場合) が**srv_sendrow**と共に送信される前または後に、任意の順序で呼び出すことができます。 完了ステータスが**srv_senddone**と共に送信される前に、すべてのメッセージをクライアントに送信する必要があります。  
  
-   **srv_sendrow** 関数は、クライアントに送信される各行につき 1 回呼び出されます。 すべての行は、メッセージ、状態値、または完了状態を**srv_sendmsg**と共に送信する前にクライアントに送信する必要があります。また、 **srv_pfield**または**srv_senddone**の**srv_status**引数を使用して送信する必要があります。  
  
-   **Srv_describe**ですべての列が定義されていない行を送信すると、アプリケーションで情報エラーメッセージが生成され、クライアントに FAIL が返されます。 この場合、その行は送信されません。  
  
## <a name="see-also"></a>参照  
 [拡張ストアド プロシージャの作成](creating-extended-stored-procedures.md)  
  
  
