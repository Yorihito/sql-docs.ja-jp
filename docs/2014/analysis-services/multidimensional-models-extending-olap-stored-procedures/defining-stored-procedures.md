---
title: ストアドプロシージャの定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545414"
---
# <a name="defining-stored-procedures"></a>ストアド プロシージャの定義
  ストアドプロシージャを使用すると、から外部ルーチンを呼び出すことができ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 ストアド プロシージャによって呼び出される外部ルーチンは、C、C++、C#、Visual Basic、Visual Basic .NET などの共通言語ランタイム (CLR) 言語でも書き込むことができます。 ストアド プロシージャを作成すると、他のストアド プロシージャ、計算されるメジャー、クライアント アプリケーションなどの多くのコンテキストから呼び出すことができます。 ストアド プロシージャを使用すると、共通コードを開発し、1 つの場所に格納できるようにすることによって、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの開発および実装が簡単になります。 ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。  
  
 このセクションでは、ストアド プロシージャの理解、デザイン、および実装に必要な情報を提供します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[ストアド プロシージャのデザイン](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用するアセンブリをデザインする方法を説明します。|  
|[ストアド プロシージャの作成](creating-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリを構成する方法を説明します。|  
|[ストアド プロシージャを呼び出す](calling-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でアセンブリを使用する方法の詳細について説明します。|  
|[ストアド プロシージャのクエリ コンテキストへのアクセス](accessing-query-context-in-stored-procedures.md)|スコープ、およびアセンブリを持つコンテキスト情報にアクセスする方法を説明します。|  
|[ストアド プロシージャのセキュリティの設定](setting-security-for-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリのセキュリティを構成する方法を説明します。|  
|[デバッグ系のストアド プロシージャ](debugging-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリをデバッグする方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
