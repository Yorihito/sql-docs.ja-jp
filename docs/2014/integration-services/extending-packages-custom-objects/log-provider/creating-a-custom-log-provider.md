---
title: カスタム ログ プロバイダーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f382500373abe5dd35380c2ad901362c44d26413
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427509"
---
# <a name="creating-a-custom-log-provider"></a>カスタム ログ プロバイダーの作成
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイム環境には広範なログ記録機能があります。 ログを使用すると、パッケージの実行中に発生するイベントをキャプチャできます。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、さまざまなログ プロバイダーを使用でき、ログを作成して XML、テキスト、データベースなどの形式で保存したり、Windows イベント ログに格納したりできます。 これらのログ プロバイダーまたは出力形式の中に要件を満たすものがない場合は、カスタム ログ プロバイダーを作成できます。

 カスタム ログ プロバイダーの作成手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。

-   基本クラスを継承する新しいクラスを作成します。 ログ プロバイダー用の基本クラスは <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> です。

-   クラスに、オブジェクトの種類を識別する属性を適用します。 ログ プロバイダー用の属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> です。

-   基本クラスのメソッドとプロパティの実装をオーバーライドします。 ログ プロバイダーでは、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティ、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッド、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッド、および <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> メソッドが対象です。

-   カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。

## <a name="getting-started-with-a-custom-log-provider"></a>カスタム ログ プロバイダーの概要

### <a name="creating-projects-and-classes"></a>プロジェクトおよびクラスの作成
 すべてのマネージド ログ プロバイダーは <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスから派生するため、カスタム ログ プロバイダーを作成するには、最初に任意のマネージド プログラミング言語でクラス ライブラリ プロジェクトを作成し、基本クラスを継承するクラスを作成します。 この派生クラスで、基本クラスのメソッドとプロパティをオーバーライドして、カスタム機能を実装します。

 プロジェクトを構成し、生成するアセンブリを厳密な名前のキー ファイルで署名します。

> [!NOTE]
>  多くの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ログ プロバイダーには、カスタム ユーザー インターフェイスがあります。カスタム ユーザー インターフェイスには <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> が実装され、**[SSIS ログの構成]** ダイアログ ボックスの **[構成]** ボックスが、使用可能な接続マネージャーがフィルター選択されたドロップダウン リストに置き換えられます。 ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。

### <a name="applying-the-dtslogprovider-attribute"></a>DtsLogProvider 属性の適用
 作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性を適用して、そのクラスがログ プロバイダーとして識別されるようにします。 この属性には、ログ プロバイダーの名前や説明など、デザイン時の情報を指定します。 `DisplayName` `Description` 属性のプロパティとプロパティは、 **Name** `Description` 「」でパッケージのログ記録を構成するときに表示される [ **SSIS ログの構成**] エディターに表示される名前と列に対応し [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] ます。

> [!IMPORTANT]
>  この属性の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> プロパティは使用されません。 ただし、このプロパティには値を入力する必要があります。そうしないと、使用可能なログ プロバイダーの一覧にカスタム ログ プロバイダーが表示されません。

> [!NOTE]
>  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは実装されていません。そのため、<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> プロパティに値を指定しても、影響がありません。

```vb
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _
Public Class MyLogProvider
     Inherits LogProviderBase
    ' TODO: Override the base class methods.
End Class
```

```csharp
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]
public class MyLogProvider : LogProviderBase
{
    // TODO: Override the base class methods.
}
```

## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>カスタム ログ プロバイダーの作成、配置、およびデバッグ
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] でカスタム ログ プロバイダーを作成、配置、およびデバッグする手順は、その他の種類のカスタム オブジェクトで必要な手順とほとんど同様です。 詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../building-deploying-and-debugging-custom-objects.md)」を参照してください。

![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。

## <a name="see-also"></a>関連項目
 カスタムログ[プロバイダーのコーディング](coding-a-custom-log-provider.md)カスタム[ログプロバイダーのユーザーインターフェイスを開発](developing-a-user-interface-for-a-custom-log-provider.md)する


