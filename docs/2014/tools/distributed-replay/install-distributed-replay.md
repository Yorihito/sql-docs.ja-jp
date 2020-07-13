---
title: コマンドプロンプトから分散再生をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 849f1a549a45b9c7e640b536e3f6ebe93a9c1b40
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054424"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a>コマンド プロンプトからの 分散再生のインストール
  分散再生の新しいインスタンスをコマンド プロンプトでインストールすると、インストールする機能とその機能の構成を指定できます。 コマンド プロンプトによるインストールでは、分散再生ユーティリティ コンポーネントのインストール、修復、アップグレード、およびアンインストールがサポートされています。 コマンド プロンプトを使用してインストールする場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、/Q パラメーターを使用した Full Quiet モードがサポートされます。  
  
> [!NOTE]  
>  ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。  
  
## <a name="installation-parameters"></a>インストール パラメーター  
 最上位の機能には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、ツールなどがあります。 ツール機能により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツール、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブック、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、およびその他の共有コンポーネントがインストールされます。 分散再生コンポーネントをインストールするには、次のパラメーターを指定します。  
  
|コンポーネント|パラメーター|  
|---------------|---------------|  
|[分散再生コントローラー]|**DREPLAY_CTLR**|  
|[分散再生クライアント]|**DREPLAY_CLT**|  
|管理ツール|**ツール**|  
  
> [!IMPORTANT]  
>  分散再生をインストールした後、コントローラー コンピューターとクライアント コンピューターのファイアウォール ルールを作成し、ターゲット サーバー上で各クライアント コンピューターの権限を付与する必要があります。 詳細については、「 [インストール後の手順の実行](complete-the-post-installation-steps.md)」を参照してください。  
  
 次の表に示すパラメーターは、インストール用のコマンド ライン スクリプトを作成する場合に使用します。  
  
|パラメーター|説明|サポートされる値|  
|---------------|-----------------|----------------------|  
|/CTLRSVCACCOUNT<br /><br /> **Optional**|分散再生コントローラー サービスのサービス アカウント。|アカウントとパスワードのチェック|  
|/CTLRSVCPASSWORD<br /><br /> **Optional**|分散再生コントローラー のサービス アカウントのパスワード。|アカウントとパスワードのチェック|  
|/CTLRSTARTUPTYPE<br /><br /> **Optional**|分散再生コントローラー サービスのスタートアップの種類。|自動<br /><br /> 無効<br /><br /> マニュアル|  
|/CTLRUSERS<br /><br /> **Optional**|分散再生コントローラー サービスの権限を持つユーザーを指定します。|区切り記号に " " (スペース) を使用した、一連のユーザー アカウント文字列<br /><br /> **重要**:分散再生コントローラー サービスを構成するとき、分散再生クライアント サービスの実行に使用する 1 つまたは複数のユーザー アカウントを指定できます。 サポートされているアカウントの一覧を次に示します。<br /><br /> ドメイン ユーザー アカウント<br /><br /> ユーザーによって作成されたローカル ユーザー アカウント<br /><br /> 管理者<br /><br /> 仮想アカウントおよび管理されたサービス アカウント (MSA)<br /><br /> ネットワーク サービス、ローカル サービス、およびシステム<br /><br /> <br /><br /> グループ アカウント (ローカルまたはドメイン) およびその他の組み込みのアカウント (Everyone など) は使用できません。|  
|/CLTSVCACCOUNT<br /><br /> **Optional**|分散再生クライアント サービスのサービス アカウント。|アカウントとパスワードのチェック|  
|/CLTSVCPASSWORD<br /><br /> **Optional**|分散再生クライアント のサービス アカウントのパスワード。|アカウントとパスワードのチェック|  
|/CLTSTARTUPTYPE<br /><br /> **Optional**|分散再生クライアント サービスのスタートアップの種類。|自動<br /><br /> 無効<br /><br /> マニュアル|  
|/CLTCTLRNAME<br /><br /> **Optional**|分散再生クライアント サービスと通信するクライアントのコンピューター名です。||  
|/CLTWORKINGDIR<br /><br /> **Optional**|分散再生クライアント サービス用の作業ディレクトリです。|有効なパス|  
|/CLTRESULTDIR<br /><br /> **省略可能**|分散再生クライアント サービス用の結果ディレクトリです。|有効なパス|  
  
### <a name="sample-syntax"></a>サンプル構文:  
 **分散再生コントローラー コンポーネントをインストールする場合**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 **分散再生クライアント コンポーネントをインストールする場合**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  
