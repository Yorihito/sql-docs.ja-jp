---
title: ホスト保護属性と CLR 統合プログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 94b46ac1c923695abf4a8bbbb4f074f14593ddcd
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954172"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>ホスト保護属性と CLR 統合プログラミング
  CLR (共通言語ランタイム) には、.NET Framework の一部であるマネージド API (アプリケーション プログラミング インターフェイス) に、特定の属性で注釈を付けるメカニズムが用意されています。このような属性は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降) など CLR のホストのための属性です。 このような HPA (ホスト保護属性) の例としては、次のものがあります。  
  
-   `SharedState`。共有状態 (静的なクラス フィールドなど) を作成または管理する機能が API で公開されるかどうかを示します。  
  
-   `Synchronization`。スレッド間で同期を実行する機能が API で公開されるかどうかを示します。  
  
-   `ExternalProcessMgmt`。ホスト プロセスを制御する方法が API で公開されるかどうかを示します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、これらの属性が与えられると、CAS (コード アクセス セキュリティ) を使用して、ホストされた環境で許可されない HPA の一覧を指定します。 CAS 要件は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 3 つの権限セット (`SAFE`、`EXTERNAL_ACCESS`、または `UNSAFE`) のいずれかで指定します。 アセンブリをサーバーに登録する際に、`CREATE ASSEMBLY` ステートメントを使用して、これら 3 つのセキュリティ レベルのいずれかを指定します。 `SAFE` 権限セットまたは `EXTERNAL_ACCESS` 権限セット内で実行されるコードでは、`System.Security.Permissions.HostProtectionAttribute` 属性が適用される特定の型またはメンバーを使用しないようにする必要があります。 詳細については、「[アセンブリの作成](../clr-integration/assemblies/creating-an-assembly.md)」および「 [CLR 統合プログラミングモデルの制限](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)」を参照してください。  
  
 `HostProtectionAttribute` は、ホストで許可されないコード構文 (型またはメソッド) を特定するという点で、信頼性を向上するための手段がセキュリティ権限とは異なります。 `HostProtectionAttribute` を使用すると、ホストの安定性確保に役立つプログラミング モデルを適用できます。  
  
## <a name="host-protection-attributes"></a>ホスト保護属性  
 HPA は、ホスト プログラミング モデルに適合しない型またはメンバーを識別して、次に示す信頼性に対する脅威を表します (リスクの低いものから順に並べています)。  
  
-   他の場合には特に害のない脅威  
  
-   サーバーで実行されるマネージ ユーザー コードの不安定化につながる脅威  
  
-   サーバー プロセス自体の不安定化につながる脅威  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、、、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` またはの値を持つ列挙体を指定するを持つ型またはメンバーの使用を許可し `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` `SharedState` `Synchronization` `UI` ません。 これにより、状態の共有を可能にしたり、同期を実行するメンバーをアセンブリから呼び出すことができなくなります。さらに、終了時にリソース リークを発生させたり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの整合性に影響を与える可能性があるメンバーの呼び出しも禁止されます。  
  
### <a name="disallowed-types-and-members"></a>禁止されている型とメンバー  
 次のトピックでは、`HostProtectionResource` の値が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって許可されない型およびメンバーを示します。  
  
> [!NOTE]  
>  各トピックに含まれる一覧は、サポートされているアセンブリから作成されたものです。  詳細については、「[サポートされている .NET Framework ライブラリ](../clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Microsoft.VisualBasic.dll の許可されない型およびメンバー](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 HPA の値が許可されない Microsoft.VisualBasic.dll の型およびメンバーの一覧を示します。  
  
 [mscorlib.dll の許可されない型およびメンバー](disallowed-types-and-members-in-mscorlib-dll.md)  
 HPA の値が許可されない mscorlib.dll の型およびメンバーの一覧を示します。  
  
 [System.dll の許可されない型およびメンバー](disallowed-types-and-members-in-system-dll.md)  
 HPA の値が許可されない System.dll の型およびメンバーの一覧を示します。  
  
 [System.Data.dll の許可されない型およびメンバー](disallowed-types-and-members-in-system-data-dll.md)  
 HPA の値が許可されない System.Data.dll の型およびメンバーの一覧を示します。  
  
 [System.Core.dll の許可されない型およびメンバー](disallowed-types-and-members-in-system-core-dll.md)  
 HPA の値が許可されない System.Core.dll の型およびメンバーの一覧を示します。  
  
## <a name="see-also"></a>参照  
 [CLR 統合のコードアクセスセキュリティ](../clr-integration/security/clr-integration-code-access-security.md)   
 [CLR 統合プログラミングモデルの制限事項](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [アセンブリの作成](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
