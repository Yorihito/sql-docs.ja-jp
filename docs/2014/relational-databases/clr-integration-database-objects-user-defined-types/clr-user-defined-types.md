---
title: CLR ユーザー定義型 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: 61f4d13550fa1812e6de3fdc98a8e4e4113fe5bd
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970721"
---
# <a name="clr-user-defined-types"></a>CLR ユーザー定義型
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、.NET Framework CLR (共通言語ランタイム) で作成されているアセンブリでプログラミングしたデータベース オブジェクトを作成できます。 CLR で用意された豊富なプログラミング モデルを使用できるデータベース オブジェクトには、トリガー、ストアド プロシージャ、関数、集計関数、型などがあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CLR コードを実行する機能が既定で無効になっています。 CLR を有効にするには、 **sp_configure**システムストアドプロシージャを使用します。  
  
 以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、ユーザー定義型 (udt) を使用してサーバーのスカラー型システムを拡張し、データベース内の CLR オブジェクトのストレージを有効にすることができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型で構成される従来の別名データ型とは異なり、UDT には複数の要素や複数の動作を含めることができます。  
  
 UDT はシステム全体からアクセスされるので、UDT を複合データ型に使用すると、パフォーマンスに悪影響を与えることがあります。 通常、複合データは従来の行やテーブルを使用する場合に最適になるようにモデル化されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の UDT は、次のような場合に適しています。  
  
-   日付型、時刻型、通貨型、および拡張数値型  
  
-   地理空間アプリケーション  
  
-   エンコードされたデータまたは暗号化されたデータ  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で UDT を開発する処理は、次の手順から構成されています。  
  
1.  **UDT を定義するアセンブリをコーディングしてビルドします。** UDT は、検証可能なコードを生成する .NET Framework 共通言語ランタイム (CLR) でサポートされる任意の言語を使用して定義されます。 このような言語には、Visual C# や Visual Basic .NET があります。 データは、.NET Framework のクラスまたは構造体のフィールドやプロパティとして公開され、動作はクラスまたは構造体のメソッドによって定義されます。  
  
2.  **アセンブリを登録します。** UDT は、Visual Studio のユーザー インターフェイスを使用してデータベース プロジェクトに配置することも、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY ステートメントを使用して、クラスまたは構造体を含むアセンブリをデータベースにコピーすることもできます。  
  
3.  **SQL Server で UDT を作成します。** アセンブリがホスト データベースに読み込まれた後、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE ステートメントを使用して UDT を作成し、UDT のメンバーとしてクラスまたは構造体のメンバーを公開します。 UDT は 1 つのデータベースのコンテキストにのみ存在します。UDT はいったん登録されると、作成時のベースとなっていた外部ファイルに対する依存関係がなくなります。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは、.NET Framework アセンブリから作成された UDT がサポートされていませんでした。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_addtype**を使用して別名データ型を使用することもできます。 CREATE TYPE 構文を使用すると、ネイティブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー定義データ型と UDT の両方を作成できます。  
  
4.  **UDT を使用してテーブル、変数、またはパラメーターを作成する**以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、ユーザー定義型は、テーブルの列定義、バッチ内の変数、 [!INCLUDE[tsql](../../includes/tsql-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数やストアドプロシージャの引数として使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ユーザー定義型を作成する](creating-user-defined-types.md)  
 UDT の作成方法について説明します。  
  
 [SQL Server でのユーザー定義型の登録](registering-user-defined-types-in-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での UDT の登録方法と管理方法について説明します。  
  
 [SQL Server でのユーザー定義型の使用](working-with-user-defined-types-in-sql-server.md)  
 UDT を使用してクエリを作成する方法について説明します。  
  
 [ADO.NET でのユーザー定義型へのアクセス](accessing-user-defined-types-in-ado-net.md)  
 ADO.NET の .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して UDT を操作する方法について説明します。  
  
  
