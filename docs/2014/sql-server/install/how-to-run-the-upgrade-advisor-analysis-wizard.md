---
title: アップグレードアドバイザー分析ウィザードを実行する方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 548abb55ffcf6b8b0eca4ab7052a7995ef271a54
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059278"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>アップグレード アドバイザー分析ウィザードを実行する方法
  アップグレード アドバイザー分析ウィザードは、アップグレード アドバイザー開始ページから起動します。 ここでは、アップグレード アドバイザー分析ウィザードの実行方法について説明します。  
  
> [!IMPORTANT]
>  アップグレード アドバイザー分析ウィザードを実行すると、アップグレード アドバイザーによって既定のレポート フォルダーにレポートが保存されます。 ただし、レポート ビューアーで表示されるのは、保存されている最近 5 件のレポートのみです。 レポートの既定の場所は、My Documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports. です。  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>アップグレードアドバイザー分析ウィザードを実行するには  
  
1.  アップグレードアドバイザーの開始ページで、[**アップグレードアドバイザー分析ウィザードの起動**] をクリックします。  
  
2.  [ ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント**] ページで、スキャンするサーバーの名前を [**サーバー名**] ボックスに入力し、[**検出**] をクリックします。 サーバー名については次のガイドラインに従ってください。  
  
    -   クラスター化されていないインスタンスをスキャンするには、コンピューター名を入力します。  
  
    -   クラスター化されたインスタンスをスキャンするには、仮想 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名を入力します。  
  
    -   クラスターのノードにインストールされている非クラスター化コンポーネントをスキャンするには、ノード名を入力します。  
  
    > [!WARNING]  
    >  アップグレード アドバイザーは、クライアント接続に標準ポート (1433) を使用するように設定されていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスには接続できません。 標準ポート (1433) を使用していない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するには、IP アドレスとポートを使用して別名を作成します。 クライアントプロトコルの構成とインスタンスの別名の作成の詳細について [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、「[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md)」を参照してください。  
    >   
    >  アップグレードアドバイザーを実行しているコンピューターにがインストールされていない場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、[**開始**] をクリックし、を実行し `cliconfg` ます。 [ ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントネットワークユーティリティ**] ダイアログボックスが開きます。 エイリアスを作成するには、[**別名**] タブを使用します。  
  
3.  検出されたコンポーネントの一覧を確認し、必要に応じて選択内容を変更して、[**次へ**] をクリックします。  
  
4.  [**接続パラメーター** ] ページで、スキャンするインスタンスを選択し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、認証方法を選択します。必要に応じて、ユーザー名とパスワードの情報を入力し、[**次へ**] をクリックします。  
  
     既定のインスタンス名は MSSQLSERVER です。  
  
5.  選択したコンポーネントに対し、必要な情報を入力します。 個々のダイアログボックスの詳細については、「 [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)」を参照してください。  
  
6.  [**アップグレードアドバイザーの設定の確認**] ページで、入力した情報を確認します。 アップグレードレポートを送信する場合は、[**レポートをに [!INCLUDE[msCoName](../../includes/msconame-md.md)] 送信**する] を選択します。 プライバシー ポリシーを確認することもできます。  
  
7.  [**実行**] をクリックして、のインスタンスを分析し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
8.  分析が完了したら、[**レポートの起動**] をクリックして、検出されたアップグレードの問題を確認します。  
  
## <a name="see-also"></a>参照  
 [方法: アップグレードアドバイザーを起動する](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [アップグレードアドバイザー &#40;ユーザーインターフェイス&#41;を実行しています](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
