---
title: WMI プロバイダーを使用した構成管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b4a4c956f1bf60f6d874ee2bda3b261dd954836d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048857"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>WMI Provider for Configuration Management の操作
  WMI Provider for Computer Management を使用したプログラミングを行う前に、次の点について考慮してください。  
  
## <a name="binding"></a>バインド  
  WMI Provider for Configuration Management は、COM オブジェクト モデルであり、事前バインドも遅延バインドもサポートしています。 遅延バインドを行う場合、VBScript などのスクリプト言語を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、別名をプログラムで操作することができます。  
  
 スクリプト言語を使用した WMI プロバイダー実装のプログラミングの詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web サイト](https://go.microsoft.com/fwlink/?linkid=15426)を参照してください。  
  
## <a name="specifying-a-connection-string"></a>接続文字列の指定  
 アプリケーションは、プロバイダーによって定義された WMI 名前空間に接続することで、WMI Provider for Configuration Management を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにダイレクトします。 Windows WMI サービスは、この名前空間をプロバイダー DLL にマップし、これをメモリに読み込みます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはすべて、1 つの WMI 名前空間で表されます。 名前空間の既定値は次のとおりです。  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 `instance_name` の既定値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインストール内の `MSSQLSERVER` になります。  
  
 **注:** Windows ファイアウォールを介して接続している場合は、コンピューターが適切に構成されていることを確認する必要があります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]MSDN [Web サイト](https://go.microsoft.com/fwlink/?linkid=15426)の Windows Management Instrumentation のドキュメントで、Windows ファイアウォール経由の接続に関する記事を参照してください。  
  
## <a name="permissions-and-server-authentication"></a>権限とサーバー認証  
 WMI Provider for Configuration Management にアクセスするには、クライアント WMI 管理スクリプトが、ターゲット コンピューター上の管理者のコンテキストで実行されている必要があります。 アクセスするユーザーは、管理するコンピューターのローカル Windows 管理者グループのメンバーである必要があります。  
  
 管理者は、グループ ポリシーを設定して、WMI プロバイダーへのユーザー アクセスを制御することができます。 グループ ポリシーの設定の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのヘルプの「グループ ポリシーと MMC」を参照してください。  
  
 WMI 管理スクリプトを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されるアカウントを更新することができます。  
  
 WMI Provider for Configuration Management では、セキュリティ証明書がサポートされています。 証明書の詳細については、「 [Encryption Hierarchy](../security/encryption/encryption-hierarchy.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 構成マネージャー](../sql-server-configuration-manager.md)  
  
  
