---
title: 拡張ストアドプロシージャのしくみ |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 02a1c64974fdcab5a686a61ac35a3a2175e16314
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758080"
---
# <a name="how-extended-stored-procedures-work"></a>拡張ストアド プロシージャのしくみ

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 拡張ストアド プロシージャが動作するプロセスは次のとおりです。  
  
1.  クライアントが拡張ストアドプロシージャを実行すると、要求はクライアントアプリケーションからに表形式のデータストリーム (TDS) 形式または Simple Object Access Protocol (SOAP) 形式で送信され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は拡張ストアド プロシージャに関連付けられた DLL を検索し、対象の DLL がまだロードされていない場合はロードします。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、要求されている拡張ストアド プロシージャ (DLL 内に関数として実装されている) を呼び出します。  
  
4.  拡張ストアド プロシージャは拡張ストアド プロシージャ API を介してサーバーに結果セットを渡し、パラメーターを返します。  

