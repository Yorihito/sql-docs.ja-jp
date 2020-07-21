---
title: CLR 統合プログラミングモデルの制限 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b9385d9b801ee615a377a78a44e087589a581ac
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953482"
---
# <a name="clr-integration-programming-model-restrictions"></a>CLR 統合プログラミング モデルの制限事項
  マネージストアドプロシージャまたはその他のマネージデータベースオブジェクトを構築するときに、によって実行される特定のコードチェックでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マネージコードアセンブリが最初にデータベースに登録されたとき、ステートメントを使用して、実行時にもチェックが実行され `CREATE ASSEMBLY` ます。 マネージド コードが実行時にもチェックされるのは、実行時に決して到達しないコード パスがアセンブリに含まれる場合があるためです。  このチェックにより、サード パーティ アセンブリを柔軟に登録できます。特に、クライアント環境での実行を目的に作成され、ホストされた CLR では実行されない "安全でない" コードを含むアセンブリをブロックしないようにすることができるため、サード パーティ アセンブリに柔軟に対応できます。 マネージコードが満たす必要のある要件は、アセンブリが、、またはのいずれかとして登録されているかどうかによって異なり、以下に示すようになり `SAFE` `EXTERNAL_ACCESS` `UNSAFE` `SAFE` ます。  
  
 マネージド コード アセンブリには、制限事項に加えてコード セキュリティ権限も付与されます。 共通言語ランタイム (CLR) では、マネージド コードに対してコード アクセス セキュリティ (CAS) というセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 `SAFE`、`EXTERNAL_ACCESS`、および `UNSAFE` の各アセンブリには、それぞれ異なる CAS 権限が付与されます。 詳細については、「 [CLR 統合コードアクセスセキュリティ](../security/clr-integration-code-access-security.md)」を参照してください。  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY チェック  
 `CREATE ASSEMBLY` ステートメントを実行する際には、セキュリティ レベルごとに次のチェックが実行されます。  いずれかのチェックが失敗した場合、`CREATE ASSEMBLY` が失敗し、エラー メッセージが表示されます。  
  
### <a name="global-any-security-level"></a>グローバル (すべてのセキュリティ レベル)  
 参照されるすべてのアセンブリは、次の条件のうち 1 つ以上を満たす必要があります。  
  
-   既にデータベースに登録されていること。  
  
-   サポートされているアセンブリの 1 つであること。 詳細については、「[サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md)」を参照してください。  
  
-   を使用し、参照されている `CREATE ASSEMBLY FROM` * \<location> *すべてのアセンブリとその依存関係をで使用できるようにし *\<location>* ます。  
  
-   を使用していて、 `CREATE ASSEMBLY FROM` すべての参照が空白で区切られたバイトを使用* \<bytes ...> して*指定されている。  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 すべての `EXTERNAL_ACCESS` アセンブリは、次の条件を満たす必要があります。  
  
-   静的フィールドが情報の格納に使用されていないこと。 読み取り専用の静的フィールドは許可されます。  
  
-   PEVerify テストにパスしていること。 .NET Framework SDK には、MSIL コードと関連メタデータがタイプ セーフの要件を満たしていることをチェックするための PEVerify ツール (peverify.exe) が付属しています。  
  
-   `SynchronizationAttribute` クラスなどによる同期が使用されていないこと。  
  
-   ファイナライザー メソッドが使用されていないこと。  
  
 `EXTERNAL_ACCESS` アセンブリでは、次のカスタム属性が許可されません。  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   `EXTERNAL_ACCESS` アセンブリの条件がすべてチェックされていること。  
  
## <a name="runtime-checks"></a>ランタイムチェック  
 コード アセンブリは、実行時に次の条件をチェックされます。 これらの条件のいずれかが見つからなかった場合、マネージド コードの実行が失敗し、例外がスローされます。  
  
### <a name="unsafe"></a>UNSAFE  
 バイト配列からメソッドを呼び出すことによって明示的に、 `System.Reflection.Assembly.Load()` または名前空間を使用して暗黙的にアセンブリを読み込むことは許可されて `Reflection.Emit` いません。  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 `UNSAFE` の条件がすべてチェックされていること。  
  
 サポートされているアセンブリの一覧の中で、次のホスト保護属性 (HPA) 値で注釈を付けられている型およびメンバーはすべて許可されません。  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   同期  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 HPAs と、サポートされているアセンブリの許可されていない型およびメンバーの一覧については、「[ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)」を参照してください。  
  
### <a name="safe"></a>SAFE  
 `EXTERNAL_ACCESS` の条件がすべてチェックされていること。  
  
## <a name="see-also"></a>参照  
 [サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md)   
 [CLR 統合のコードアクセスセキュリティ](../security/clr-integration-code-access-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [アセンブリの作成](../assemblies/creating-an-assembly.md)  
  
  
