---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae11fbccaa4f577815e503d9a0dffaa34c7c04ed
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723606"
---
# <a name="mssqlserver_33028"></a>MSSQLSERVER_33028
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|33028|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_CRYPTOPROV_CANTOPENSESSION|  
|メッセージ テキスト|%S_MSG '%.*ls' のセッションを開くことができません。 プロバイダー エラー コード: %d。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、エラー メッセージに表示されている暗号化サービス プロバイダーを開くことができませんでした。 暗号化サービス プロバイダーは、表示されているエラー コードを返しました。 エラーの詳細については、暗号化サービス プロバイダーに問い合わせる必要があります。  
  
|エラー コード|説明|  
|--------------|---------------|  
|0|正常終了しました。 エラーなし。|  
|1|失敗しました。 未定義のエラーまたは予期しないエラーが発生しました。 追加情報は入手できません。|  
|2|バッファーが不足しています。 暗号化サービス プロバイダー用の領域を割り当てることができませんでした。|  
|3|サポートされていません。 問題となる暗号化サービス プロバイダーが、このリリースではサポートされていません。 別の暗号化サービス プロバイダーを選択してください。|  
|4|Not Found. (見つかりませんでした。) 指定した暗号化サービス プロバイダーが存在しないか、ファイルにアクセスする承認を得ていません。|  
|5|承認エラーです。 資格情報の作成時に指定したパスワードまたはユーザー名が正しくないか、 資格情報が存在しない可能性があります。|  
|6|引数が無効です。 暗号化サービス プロバイダーに無効な引数が渡されました。|  
  
## <a name="user-action"></a>ユーザーの操作  
エラーを解決するか、暗号化サービス プロバイダーに詳細を問い合わせてください。  
  
