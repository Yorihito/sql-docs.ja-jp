---
title: ローカル実行とリモート実行の相違点について | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 730dcaf8e22ad5bd4a26ada35d89e5fb02b60c37
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422569"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>ローカル実行とリモート実行の相違点について
  パッケージの開発者および管理者は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行場所に関連する制限があることを知っておく必要があります。  
  
-   **パッケージは、パッケージを起動するプログラムと同じコンピューターで実行されます**。 プログラムが別のサーバー上にリモートに格納されたパッケージを読み込む場合であっても、そのパッケージはローカル コンピューターで実行されます。  
  
-   **パッケージを開発環境の外部で実行することができるのは、そのコンピューターに Integration Services がインストールされている場合のみです**。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がインストールされていないクライアント コンピューターでは、パッケージを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の外部で実行することはできません。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ライセンスの条項により、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を他のコンピューターにインストールすることは許可されない場合があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はサーバー コンポーネントであるため、クライアント コンピューターに再配布できません。 クライアント コンピューターからパッケージを実行するには、パッケージが確実にサーバー上で実行される方法で、パッケージを起動する必要があります。  
  
 保存済みパッケージの読み込みと実行の詳細については、次のトピックを参照してください。  
  
-   [プログラムによるローカル パッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [プログラムによるリモート パッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 保存済みパッケージの実行と、その出力のカスタム プログラムへの読み込みの詳細については、次のトピックを参照してください。  
  
-   [ローカル パッケージの出力の読み込み](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>関連項目  
 [プログラムによるローカルパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [プログラムによるリモートパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [ローカル パッケージの出力の読み込み](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
