---
title: CLR ユーザー定義集計 |Microsoft Docs
description: SQL Server CLR 統合を使用すると、マネージコードでカスタム集計関数を作成して、値のセットに対して計算を実行し、値を返すことができます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: 6775e9f4bda98f970fd5cdb666fb0bfdb8c1ac10
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727873"
---
# <a name="clr-user-defined-aggregates"></a>CLR ユーザー定義集計
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  集計関数は、値の集まりに対して計算を実行し、1 つの値を返します。 従来、で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、入力スカラー値のセットに対して演算を実行し、そのセットから1つの集計値を生成する、組み込みの集計関数 ( **SUM** 、 **MAX**など) のみがサポートされていました。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) と統合されたことにより、開発者はマネージド コードでカスタム集計関数を作成し、[!INCLUDE[tsql](../../includes/tsql-md.md)] や他のマネージド コードから作成した関数にアクセスできるようになりました。  
  
 次の表に、このセクションの各トピックの一覧を示します。  
  
 [CLR ユーザー定義集計の要件](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 CLR ユーザー定義集計関数の実装要件の概要について説明します。  
  
 [CLR ユーザー定義集計関数の呼び出し](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 ユーザー定義集計を呼び出す方法について説明します。  
  
  
