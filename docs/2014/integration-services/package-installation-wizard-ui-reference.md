---
title: パッケージインストールウィザードの UI リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.deploymentwizard.confirminstallation.f1
- sql12.dts.deploymentwizard.deploydtspackages.f1
- sql12.dts.deploymentwizard.selectinstfolder.f1
- sql12.dts.deploymentwizard.specifytargetsqlserver.f1
- sql12.dts.deploymentwizard.welcome.f1
- sql12.dts.deploymentwizard.finish.f1
- sql12.dts.deploymentwizard.configurepackages.f1
- sql12.dts.deploymentwizard.packagevalidation.f1
helpviewer_keywords:
- Package Installer Wizard
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc500615774a67bae70e9c9fa8845db166f44466
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423879"
---
# <a name="package-installation-wizard-ui-reference"></a>パッケージ インストール ウィザードの UI リファレンス
  **パッケージ インストール ウィザード** を使用すると、プロジェクトに含まれるパッケージおよびその他のファイル、パッケージの従属ファイルを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。  
  
 パッケージを配置する前に、構成を作成してパッケージに配置できます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は構成を使用して、パッケージのプロパティとパッケージ オブジェクトを実行時に動的に更新します。 たとえば、接続文字列が含まれるプロパティに値をマップする構成を使用して、実行時に OLE DB 接続の接続文字列を動的に設定できます。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを構築して配置ユーティリティを作成するまでは、パッケージ インストール ウィザードは実行できません。 詳細については、「 [配置ユーティリティを使用してパッケージを配置する](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)」を参照してください。  
  
 ここでは、ウィザードの各ページについて説明します。  
  
## <a name="welcome-to-the-package-installation-wizard-page"></a>[パッケージ インストール ウィザードへようこそ] ページ  
 **パッケージ インストール ウィザード** を使用すると、パッケージ配置ユーティリティを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。  
  
 **次回からこの開始ページを表示しない**  
 ウィザードを再度実行するときに開始ページをスキップします。  
  
 **次へ**  
 ウィザードの次のページに進みます。  
  
 **完了**  
 [パッケージ インストール ウィザードの完了] ページまでスキップします。 ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。  
  
## <a name="configure-packages-page"></a>[パッケージの構成] ページ  
 **[パッケージの構成]** ページを使用すると、パッケージ構成を編集できます。  
  
### <a name="options"></a>オプション  
 **構成ファイル**  
 一覧からファイルを選択して、構成ファイルの内容を編集します。  
  
 **Related Topics:** [Create Package Configurations](../../2014/integration-services/create-package-configurations.md)  
  
 **パス**  
 構成するプロパティのパスを表示します。  
  
 **Type**  
 プロパティのデータ型が表示されます。  
  
 **Value**  
 構成の値を指定します。  
  
 **次へ**  
 ウィザードの次のページに進みます。  
  
 **完了**  
 [パッケージ インストール ウィザードの完了] ページまでスキップします。 ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。  
  
## <a name="confirm-installation-page"></a>[インストールの確認] ページ  
 **[インストールの確認]** ページを使用して、パッケージのインストールの開始、状態の表示、およびウィザードが指定されたプロジェクトからファイルをインストールするために使用する情報の表示を行います。  
  
 **次へ**  
 パッケージとその依存関係をインストールし、インストールが完了したらウィザードの次のページへ移動します。  
  
 **状態**  
 パッケージ インストールの進行状況を表示します。  
  
 **完了**  
 [パッケージ インストール ウィザードの完了] ページに移動します。 ウィザード ページを戻って選択内容を変更し、必要なオプションをすべて指定した場合は、このオプションを使用します。  
  
## <a name="deploy-ssis-packages-page"></a>[SSIS パッケージの配置] ページ  
 **[SSIS パッケージの配置]** ページを使用して、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージとその従属ファイルをインストールする場所を指定します。  
  
### <a name="options"></a>オプション  
 **[ファイル システムに配置]**  
 パッケージとその従属ファイルをファイル システム上の指定したフォルダーに配置します。  
  
 **[SQL Server に配置]**  
 パッケージとその従属ファイルを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに配置します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がサーバー間でパッケージを共有している場合に、このオプションを使用します。 パッケージの従属ファイルは、すべてファイル システムの指定フォルダーにインストールされます。  
  
 **[インストール後にパッケージを検証する]**  
 インストール後にパッケージを検証するかどうかを指定します。  
  
 **次へ**  
 ウィザードの次のページに進みます。  
  
 **完了**  
 [パッケージ インストール ウィザードの完了] ページまでスキップします。 ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。  
  
## <a name="packages-validation-page"></a>[パッケージの検証] ページ  
 **[パッケージの検証]** ページを使用して、パッケージ検証の進行と結果を表示します。  
  
 **次へ**  
 ウィザードの次のページに進みます。  
  
## <a name="select-installation-folder-page"></a>[インストール フォルダーの選択] ページ  
 **[インストール フォルダーの選択]** ページを使用して、パッケージとその従属ファイルをインストールするファイル システム フォルダーを指定します。  
  
### <a name="options"></a>オプション  
 **フォルダー**  
 パッケージとその従属ファイルをコピーするパスとフォルダーを指定します。  
  
 **参照**  
 **[フォルダーの参照]** ダイアログ ボックスを使用して、インストール先のフォルダーを参照します。  
  
 **次へ**  
 ウィザードの次のページに進みます。  
  
 **完了**  
 [パッケージ インストール ウィザードの完了] ページまでスキップします。 指定を変えるためにウィザードのページを戻った場合、必要なオプションをすべて指定したら、このオプションを使用します。  
  
## <a name="specify-target-sql-server-page"></a>[インストール先の SQL Server の指定] ページ  
 **[インストール先の SQL Server の指定]** ページを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスへのパッケージ配置に関するオプションを指定します。  
  
### <a name="options"></a>オプション  
 **サーバー名**  
 パッケージの配置先となるサーバーの名前を指定します。  
  
 **[Windows 認証を使用する]**  
 サーバーのログオンに Windows 認証を使用するかどうかを指定します。 より高いセキュリティのためには Windows 認証をお勧めします。  
  
 **SQL Server 認証を使用する**  
 パッケージがサーバーのログオンに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用するかどうかを指定します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。  
  
 **ユーザー名**  
 ユーザー名を指定します。  
  
 **パスワード**  
 パスワードを指定します。  
  
 **パッケージ パス**  
 論理フォルダーの名前を指定するか、または既定フォルダーを使用する場合は「/」を入力します。  
  
 [ **SSIS パッケージ**] ダイアログボックスでフォルダーを選択するには、参照ボタン ([...]) をクリックします。ただし、このダイアログボックスには、既定のフォルダーを選択するための手段が用意されていません。 既定フォルダーを使用する場合は、テキスト ボックスに「/」を入力する必要があります。  
  
> [!NOTE]  
>  有効なパッケージ パスを入力しないと、"1 つ以上の引数が無効です。" というエラー メッセージが表示されます。  
  
 **[暗号化をサーバー ストレージに依存する]**  
 パッケージの安全を確保するために、 [!INCLUDE[ssDE](../includes/ssde-md.md)] のセキュリティ機能を使用する場合に選択します。  
  
 **次へ**  
 ウィザードの次のページに進みます。  
  
 **完了**  
 [パッケージ インストール ウィザードの完了] ページまでスキップします。 ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。  
  
## <a name="finish-the-package-installation-page"></a>[パッケージ インストール ウィザードの完了] ページ  
 **[パッケージ インストール ウィザードの完了]** ページを使用して、パッケージのインストール結果の要約を表示します。 このページでは、配置された [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの名前、インストールされたパッケージ、構成ファイル、インストール場所などの詳細が表示されます。  
  
 **完了**  
 **[完了]** をクリックすると、ウィザードが終了します。  
  
## <a name="see-also"></a>関連項目  
 [SSIS&#41;&#40;パッケージの配置](packages/legacy-package-deployment-ssis.md)  
  
  
