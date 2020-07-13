---
title: アップグレードアドバイザーの前提条件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062362"
---
# <a name="upgrade-advisor-prerequisites"></a>アップグレード アドバイザーの前提条件
  ここでは、アップグレード アドバイザーに関するソフトウェアの必要条件について説明します。  
  
## <a name="prerequisites"></a>前提条件  
 アップグレード アドバイザーのインストールと実行の前提条件は、次のとおりです。  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2 以降、Windows 7、または [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2。  
  
-   Windows インストーラー 4.5。 [Windows インストーラー Web サイト](https://www.microsoft.com/download/details.aspx?id=8483)から Windows インストーラーをインストールできます。  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (.NET Framework 4 以降)。 は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 製品メディア、 [SDK、再頒布可能パッケージ、Service Pack ダウンロード Web サイト](https://go.microsoft.com/fwlink/?LinkId=48882)で入手できます。  
  
    -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] メディアから .NET Framework 4 をインストールするには、ディスク ドライブのルートに移動します。 次に、redist フォルダー、DotNetFrameworks フォルダーの順にダブルクリックし、dotNetFx40_Full_x86_x64.exe (32 ビットおよび 64 ビット オペレーティング システム用) を実行します。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Scriptdom はアップグレードアドバイザーをインストールするための前提条件で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] あり、アップグレードアドバイザーのセットアップではインストールされません。 セットアップでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Feature Pack から scriptdom をダウンロードしてインストールする必要があり [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーをインストールする方法](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
