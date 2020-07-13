---
title: SQL Server Native Client プログラミング |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, about SQL Server Native Client
- SQL Server Native Client, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
- data access [SQL Server Native Client]
- SQL Server Native Client
- SQLNCLI
- native data access [SQL Server Native Client]
ms.assetid: 14ba2cb1-a424-4e4d-b224-0bf1015ab801
author: rothja
ms.author: jroth
ms.openlocfilehash: 5216f6b49b16920fe3115f3985bc05f8af2c282e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057243"
---
# <a name="sql-server-native-client-programming"></a>SQL Server Native Client プログラミング
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client とは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入された、OLE DB と ODBC の両方で使用されるスタンドアロンのデータ アクセス API (アプリケーション プログラミング インターフェイス) です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、SQL OLE DB プロバイダーと SQL ODBC ドライバーが 1 つのネイティブ DLL (ダイナミック リンク ライブラリ) に統合されています。 また、Windows Data Access Components (Windows DAC、以前の Microsoft Data Access Components (MDAC)) にはない新しい機能も用意されています。 MARS (複数のアクティブな結果セット)、UDT (ユーザー定義データ型)、クエリ通知、スナップショット分離、XML データ型のサポートなどの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で導入された機能を必要とする新しいアプリケーションを作成したり、これらの機能で既存のアプリケーションを強化するために、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Native Client を使用できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client と WINDOWS dac の相違点と、WINDOWS dac アプリケーションを Native client に更新する前に考慮すべき問題に関する情報につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [MDAC から SQL Server Native Client するためのアプリケーションの更新](applications/updating-an-application-to-sql-server-native-client-from-mdac.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、常に、Windows DAC 付属の ODBC ドライバー マネージャーと共に使用します。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、Windows DAC 付属の OLE DB Core Services と共に使用できますが、必須ではありません。OLE DB Core Services を使用するかどうかは、個々のアプリケーションの要件 (たとえば、接続プールが必要であるかどうかなど) によって異なります。  
  
 ADO (ActiveX Data Object) アプリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用できますが、ADO を使用するときは `DataTypeCompatibility` 接続文字列キーワード (またはそれに対応する `DataSource` プロパティ) を指定することをお勧めします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用すると、接続文字列のキーワード、OLE DB プロパティ、または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を経由することにより、[!INCLUDE[tsql](../../includes/tsql-md.md)] で導入された上記の新機能を ADO アプリケーションで利用できます。 ADO でこれらの機能を使用する方法の詳細については、「 [USING ado with SQL Server Native Client](applications/using-ado-with-sql-server-native-client.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client は、OLE DB または ODBC のいずれかを使用して簡単に SQL Server へのネイティブ データ アクセスを実現できるように設計されています。 OLE DB と ODBC という 2 つのテクノロジを 1 つのライブラリに統合して簡素化しただけでなく、Microsoft Windows プラットフォームの一部になっている既存の Windows DAC コンポーネントを変更することなく新しいデータ アクセス機能を導入および展開できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は WINDOWS dac のコンポーネントを使用しますが、特定のバージョンの WINDOWS dac に明示的に依存することはありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でサポートされるオペレーティング システムにインストールされているバージョンの Windows DAC と共に使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server Native Client の新機能](sql-server-native-client.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の重要な新しい機能を紹介します。  
  
 [SQL Server Native Client を使用する場合](when-to-use-sql-server-native-client.md)  
 Microsoft の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データアクセステクノロジを使用した Native Client の適合性、WINDOWS DAC と ADO.NET との比較、使用するデータアクセステクノロジを決定するためのポインターについて説明します。  
  
 [SQL Server Native Client の機能](features/sql-server-native-client-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でサポートされている機能について説明します。  
  
 [SQL Server Native Client を使用したアプリケーションのビルド](applications/building-applications-with-sql-server-native-client.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の開発における、Windows DAC との違い、使用されるコンポーネント、ADO と併用する方法などの概要を示します。  
  
 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ライブラリの再配布の方法など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のインストールと配置についても説明します。  
  
 [SQL Server Native Client のシステム要件](system-requirements-for-sql-server-native-client.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用するために必要なシステム リソースについて説明します。  
  
 [SQL Server Native Client &#40;OLE DB&#41;](ole-db/sql-server-native-client-ole-db.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの詳細について説明します。  
  
 [SQL Server Native Client &#40;ODBC&#41;](odbc/sql-server-native-client-odbc.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーの詳細について説明します。  
  
 [SQL Server Native Client に関する詳細情報](finding-more-sql-server-native-client-information.md)  
 外部リソースへのリンク、詳しい補助資料など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client についての関連情報です。  
  
 [SQL Server Native Client エラー](../native-client-ole-db-errors/errors.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client に関連するランタイム エラーについて説明します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2005 Native Client からアプリケーションを更新する](applications/updating-an-application-from-sql-server-2005-native-client.md)   
 [ODBC の操作方法に関するトピック](../native-client-odbc-how-to/odbc-how-to-topics.md)   
 [OLE DB の使用法に関するトピック](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
