---
title: 休止 SQL Server 6.5 ログインをアップグレードすることはできません |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054818"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>休止している SQL Server 6.5 ログインはアップグレードできない
  アップグレード アドバイザーによって、パスワードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に直接アップグレードできない [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ログインが検出されました。  
  
 このログインを有効にするには、パスワードをリセットする必要があります。 パスワードをリセットするには、ALTER LOGIN を使用します。  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 新しいパスワードがシステムのパスワード複雑性ポリシーを満たしているか検証されます。ポリシーのチェックが無効になっている場合は検証が行われません。 複雑なパスワードを使用し、ポリシーのチェックを無効にしないことをお勧めします。 MUST_CHANGE オプションを使用すると、新しいパスワードの選択がユーザーに強制されます。 これは必須ではありませんが、推奨されています。  
  
 次のクエリを使用すると、休止ログインを特定できます。  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
