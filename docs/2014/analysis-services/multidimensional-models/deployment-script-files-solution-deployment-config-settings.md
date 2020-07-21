---
title: ソリューション配置の構成設定を指定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
author: minewiskan
ms.author: owend
ms.openlocfilehash: 31f269e601900535c3d375ed6e76376fa2bcdf63
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546844"
---
# <a name="specifying-configuration-settings-for-solution-deployment"></a>ソリューションの配置に関する構成設定の指定
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードでは、配置スクリプトで使用するパーティションおよびロールの配置オプションを \<*project name*> configsettings ファイルから読み取ります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]は、プロジェクトのビルド時にこのファイルを作成し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]は、現在のプロジェクトの構成設定を使用して、configsettings ファイルを作成します。 \<*project name*>  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>配置に関する構成設定の確認  
 次に、configsettings ファイルに格納されている構成設定を示します。 \<*project name*>  
  
-   **データ ソース接続文字列** これは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで指定されている値に基づいた各データ ソースの接続文字列です。 このファイルに接続文字列が保存される際には、常にユーザー ID とパスワードが削除されます。 ただし、配置ウィザードで Analysis Services インスタンスに直接配置を行う場合は、ウィザードで適切なユーザー ID とパスワードを入力して、配置するデータベースを正常に処理することができます。 配置ウィザードで配置スクリプトを保存する場合、この接続情報は配置スクリプト内に保存されません。  
  
-   **権限借用アカウント** この設定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が各データ ソースでステートメントを実行するために使用するユーザー名を指定します。 権限借用アカウントが指定されていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のログオン アカウントを使用してステートメントが実行されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログオン アカウントがデータ ソース内で権限を直接与えられている場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのすべてのデータベース内のデータベース管理者は、だれでもそのログオン アカウントを使用してデータ ソースにアクセスできます。 ユーザー アカウントとパスワードが指定された場合、このファイルに権限借用情報が保存される前に常にこの情報は削除されます。 ただし、配置ウィザードで Analysis Services インスタンスに直接配置を行う場合は、ウィザードで適切なユーザー ID とパスワードを入力して、配置するデータベースを正常に処理することができます。 配置ウィザードで配置スクリプトを保存する場合、この権限借用情報は配置スクリプト内に保存されません。  
  
-   **キーのエラー ログ ファイル** この設定では、データベース内の各キューブ、メジャー グループ、パーティション、およびディメンションのキー エラー ログ ファイルのファイル名とパスを指定します。  
  
-   **ストレージの場所** この設定では、データベース内の各キューブ、メジャー グループ、およびパーティションのストレージの場所を指定します。 オブジェクトの値が指定されていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードではオブジェクトの既定の場所が使用されます。 たとえば、パーティションにはメジャー グループの場所が使用され、メジャー グループにはキューブの場所が使用され、キューブには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのオブジェクトの既定の場所が使用されます。 ストレージの場所には、ローカルまたは汎用名前付け規則 (UNC) のどちらかのパスを指定できます。  
  
-   **レポート サーバー** この設定では、データベース内の各キューブで定義されている各レポート アクションのレポート サーバーとフォルダーの場所を指定します。  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>配置に関する構成設定の変更  
 場合によっては、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] configsettings ファイルに格納されているものとは異なる構成設定を使用して、プロジェクトを配置する必要があります。 \<*project name*> たとえば、1 つまたは複数のデータ ソースへの接続文字列を変更するか、特定のパーティションまたはメジャー グループのストレージの場所を指定する必要が生じることがあります。  
  
 プロジェクト内のパーティションおよびロールの配置を変更するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] \<*project name*> 次の手順で説明するように、configsettings ファイル内でこの情報を変更する必要があります。 の [ *\<project name>* **プロパティページ**] ダイアログボックスには [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] これらのオプションが表示されないため、プロジェクト内のパーティションおよびロールの設定を変更することはできません。  
  
> [!NOTE]  
>  構成設定は、すべてのオブジェクトに適用することも、新たに作成したオブジェクトのみに適用することもできます。 以前に配置した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに追加のオブジェクトを配置し、既存のオブジェクトを上書きしないようにする場合は、新たに作成したオブジェクトのみに構成設定を適用します。 構成設定をすべてのオブジェクトに適用するか、新しく作成したものにのみ適用するかを指定するには、deploymentoptions ファイルでこのオプションを設定します。 \<*project name*> 詳細については、「 [パーティションおよびロールの配置オプションの指定](deployment-script-files-partition-and-role-deployment-options.md)」を参照してください。  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>入力ファイルの生成後に構成設定を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、 **[構成設定]** ページで配置するオブジェクトの構成設定を指定します。  
  
     \- または -  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     \- または -  
  
-   任意の \<*project name*> テキストエディターを使用して、configsettings ファイルを変更します。  
  
## <a name="see-also"></a>参照  
 [インストール先の指定](deployment-script-files-specifying-the-installation-target.md)   
 [パーティションおよびロールの配置オプションの指定](deployment-script-files-partition-and-role-deployment-options.md)   
 [処理オプションの指定](deployment-script-files-specifying-processing-options.md)  
  
  
