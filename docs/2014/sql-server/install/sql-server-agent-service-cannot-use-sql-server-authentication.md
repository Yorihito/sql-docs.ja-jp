---
title: SQL Server エージェントサービスは SQL Server Authentication | を使用できませんMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036249"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>SQL Server エージェント サービスで SQL Server 認証を使用できない
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは Windows 認証のみをサポートします。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、Windows 認証を使用してデータベースにログオンすることのみできます。 つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーである必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SQL Server エージェントのセキュリティ管理」および「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのセキュリティの実装」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
