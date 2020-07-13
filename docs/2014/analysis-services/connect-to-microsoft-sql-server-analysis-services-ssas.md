---
title: Microsoft SQL Server Analysis Services への接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
ms.openlocfilehash: 558f9936b7a8e78b3ef75f3bb525185ae497959c
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84526968"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a>[Microsoft SQL Server Analysis Service への接続] (SSAS)
  **テーブルのインポートウィザード**のこのページを使用すると、SharePoint でホストされている Microsoft SQL Server Analysis Services キューブまたは PowerPivot ブックからデータをインポートするための設定を指定できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。  
  
> [!NOTE]  
>  このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。 ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 **[接続の表示名]**  
 このデータ ソース接続の一意の名前を入力します。 これは必須フィールドです。  
  
 **サーバー名またはファイル名**  
 次のいずれかを入力します。  
  
-   SQL Server Analysis Services サーバーが接続に使用する名前または IP アドレスを入力します。  
  
     ピリオド (.)、(local)、または localhost を使用すると、ローカル サーバーを指定できます。  
  
-   SharePoint にパブリッシュする PowerPivot ブックの URL を入力します。  
  
 **[Windows 認証を使用する]**  
 SQL Server Analysis Services サーバーへの接続に Windows 認証を使用するかどうかを指定します。  
  
 Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。 可能であれば、Windows 認証を使用します。  
  
 Windows 認証を使用した場合、[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際に、現在のユーザーの資格情報が使用されます。 データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。  
  
 **SQL Server 認証を使用する**  
 SQL Server Analysis Services サーバーへの接続に SQL Server 認証を使用するかどうかを指定します。  
  
 SQL Server 認証の場合、SQL Server は、SQL Server ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。  
  
 SQL Server 認証は、データ ソースの接続文字列を構築するときに使用されます。 [テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。 データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。  
  
 **ユーザー名**  
 データベース接続に使用するユーザー名を指定します。 このオプションは、Windows 認証を使用した接続を選択した場合のみ使用できます。  
  
 **パスワード**  
 データベース接続に使用するパスワードを指定します。 このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ編集できます。  
  
 **[パスワードを保存する]**  
 **[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。 このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ使用できます。  
  
 **データベース名**  
 データベースを一覧から選択します。  
  
 **詳細設定**  
 **[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。 詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。  
  
 **接続をテスト**  
 現在の設定を使用して、データ ソースに対する接続の確立を試みます。 接続が正常に確立されたかどうかを示すメッセージが表示されます。  
  
  
