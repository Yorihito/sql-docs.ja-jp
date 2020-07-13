---
title: スクリプトによるパッケージの拡張 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a640847dbc6846b4045ea7f2f6ac1afe9294c160
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426019"
---
# <a name="extending-packages-with-scripting"></a>スクリプトによるパッケージの拡張
  組み込みコンポーネントの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が要件を満たしていない場合は、独自の拡張機能をコーディングすることによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の機能を拡張できます。 パッケージを拡張するには 2 つの方法があります。1 つ目は、スクリプト タスクおよびスクリプト コンポーネントによって提供される強力なラッパー内でコードを記述する方法です。2 つ目は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルによって提供される基本クラスを基にカスタム [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 拡張機能を最初から作成する方法です。

 ここでは、より簡単な方法である、スクリプトを使用したパッケージの拡張について説明します。

 スクリプト タスクおよびスクリプト コンポーネントを利用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローとデータ フローを、コードをほとんど記述することなく拡張できます。 これらの両オブジェクトでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 開発環境と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のプログラミング言語を使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリやカスタム アセンブリで提供されるすべての機能を活用できます。 スクリプト タスクおよびスクリプト コンポーネントを使用すると、カスタム タスクやカスタム データ フロー コンポーネントの開発時に通常必要となるインフラストラクチャ コードを一切記述せずにカスタム機能を作成できます。

## <a name="in-this-section"></a>このセクションの内容
 [スクリプトタスクとスクリプトコンポーネントの比較](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)スクリプトタスクとスクリプトコンポーネントの類似点と相違点について説明します。

 [スクリプトソリューションとカスタムオブジェクトの比較](comparing-scripting-solutions-and-custom-objects.md)スクリプトソリューションとカスタムオブジェクトの開発のどちらかを選択する際に使用する基準について説明します。

 [スクリプトソリューションでの他のアセンブリの参照](referencing-other-assemblies-in-scripting-solutions.md)外部アセンブリと名前空間をスクリプトプロジェクトで参照および使用するために必要な手順について説明します。

 [スクリプトタスクによるパッケージの拡張](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md)スクリプトタスクを使用してカスタムタスクを作成する方法について説明します。 通常は、パッケージの実行またはパッケージが開くデータ ソースごとにタスクが 1 回呼び出されます。

 [スクリプトコンポーネントによるデータフローの拡張](data-flow-script-component/extending-the-data-flow-with-the-script-component.md)スクリプトコンポーネントを使用して、カスタムデータフローの変換元、変換、および変換先を作成する方法について説明します。 通常は、処理するデータ行ごとにデータ フロー コンポーネントが 1 回呼び出されます。

## <a name="reference"></a>リファレンス
 [Integration Services のエラーとメッセージの参照](../integration-services-error-and-message-reference.md)定義済みの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラーコードとそのシンボル名と説明を一覧表示します。

## <a name="related-sections"></a>関連項目
 [カスタムオブジェクトを使用したパッケージの拡張](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)複数のパッケージで使用するプログラムカスタムタスク、データフローコンポーネント、およびその他のパッケージオブジェクトを作成する方法について説明します。

 [プログラムによるパッケージの作成](../building-packages-programmatically/building-packages-programmatically.md)プログラムによってパッケージを作成、構成、実行、読み込み、保存、および管理する方法について説明し [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。

![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)] が提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。

## <a name="see-also"></a>関連項目
 [SQL Server Integration Services](../sql-server-integration-services.md)


