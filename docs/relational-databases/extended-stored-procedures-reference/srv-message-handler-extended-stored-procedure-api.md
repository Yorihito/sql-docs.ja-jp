---
title: srv_message_handler (拡張ストアド プロシージャ API)
description: Srv_message_handler と、インストールされている拡張ストアドプロシージャ API メッセージハンドラーを呼び出す方法について説明します。
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_message_handler
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 2edc96558c00b43dfe9d9b346ad75c32b42af1cd
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87332358"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a>srv_message_handler (拡張ストアド プロシージャ API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 インストールされている拡張ストアド プロシージャ API メッセージ ハンドラーを呼び出します。 この関数は、通常、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張ストアドプロシージャからを呼び出して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーログファイルまたは Windows アプリケーションログにエラー (拡張ストアドプロシージャで定義) を記録するために使用され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 *srvproc* パラメーターには、アプリケーションとクライアント間の通信やデータを管理するために使用する情報が格納されます。  
  
 *errornum*  
 拡張ストアド プロシージャが定義するエラー番号です。 この値の有効値は 50,001 から 2,147,483,647 です。  
  
 *severity*  
 エラーに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の重大度を示す標準の値です。 この値の有効値は 0 ～ 24 です。  
  
 *状態*  
 エラーに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の状態値です。  
  
 *oserrnum*  
 オペレーティング システムのエラー番号です。 この引数は無視されます。  
  
 *errtext*  
 拡張ストアド プロシージャのエラー *errornum* の説明です。  
  
 *errtextlen*  
 拡張ストアド プロシージャのエラー文字列 *errtext* の長さです。  
  
 *oserrtext*  
 オペレーティング システムのエラー *oserrnum* の説明です。 この引数は無視されます。  
  
 *oserrtextlen*  
 オペレーティング システムのエラー文字列 *oserrtext* の長さです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **srv_message_handler** 関数を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の集中型エラー ログ機能とレポート機能に拡張ストアド プロシージャを統合できるようになります。 拡張ストアド プロシージャからのイベントに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の警告を設定し、警告条件を SQL Server エージェントで監視できます。  
  
 エラー メッセージが長い場合は、412 バイトに切り捨てられます。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://msdn.microsoft.com/security/)をご覧ください。  
  
  
