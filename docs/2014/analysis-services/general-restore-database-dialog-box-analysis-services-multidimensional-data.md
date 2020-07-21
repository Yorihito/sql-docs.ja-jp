---
title: '[全般] ([データベースの復元] ダイアログボックス) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 787488570627e2c8c7fc9a37e8f814847c40f3ca
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544384"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a>[全般] ([データベースの復元] ダイアログ ボックス) (Analysis Services - 多次元データ)
  **の** [データベースの復元] **ダイアログ ボックスの** [全般] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの復元に使用するバックアップ ファイルおよび全般設定を指定できます。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
 **[データベースの復元] ダイアログ ボックスで [全般] ページを表示するには**  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の **オブジェクト エクスプローラー** で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダー、またはデータベースを右クリックし、 **[データベースの復元]** をクリックします。次に、 **[ページの選択]** で **[全般]** をクリックします。  
  
## <a name="options"></a>オプション  
 **スクリプト**  
 ダイアログ ボックスで選択したオプションに基づいた復元スクリプトを作成します。 復元用スクリプトは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) で記述されています。  
  
 **[スクリプト]** アイコンをクリックすると、既定では、新しいクエリ ウィンドウに復元スクリプトが送信されます。  
  
 **[スクリプト]** の矢印をクリックすると、復元スクリプトの送信先を次の中から選択できるメニューが表示されます。  
  
-   新しいクエリ ウィンドウ (既定)。  
  
-   ファイル。  
  
-   クリップボード。  
  
-   ジョブ。  
  
 **データベースの復元**  
 復元する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを選択します。  
  
 **復元元のバックアップ ファイル**  
 選択された [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの復元元のバックアップ ファイルを選択します。  
  
 **参照**  
 クリックすると、**[データベース ファイルの検索]** ダイアログ ボックスが表示され、使用するバックアップ ファイルのパスおよびファイル名を選択できます。 **[データベース ファイルの検索]** ダイアログ ボックスの詳細については、「[[データベース ファイルの検索] ダイアログ ボックス (Analysis Services - 多次元データ)](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **[データベースの上書きを許可する]**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でこのオプションを選択すると、指定した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内の既存のオブジェクトを、指定のバックアップ ファイルの内容に戻すことができます。  
  
 **[セキュリティ情報を含める]**  
 バックアップ ファイルに格納されたすべてのセキュリティ情報を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースにコピーする場合に使用します。  
  
 このオプションを選択すると有効になるドロップダウン リストで、セキュリティ情報の量を選択できます。 次のオプションを使用できます。  
  
|オプション|説明|  
|------------|-----------------|  
|**[すべてコピー]**|バックアップ ファイルに格納されたデータベース ロール、およびロールに関連付けられたユーザー アカウントを復元します。|  
|**メンバーシップのスキップ**|バックアップ ファイルに格納されたデータベース ロールを復元しますが、ロールに関連付けられたユーザー アカウントは復元しません。|  
  
 **パスワード**  
 バックアップ ファイルが暗号化されている場合は、バックアップ ファイルの暗号化に使用されたパスワードを入力します。  
  
## <a name="see-also"></a>参照  
 [[データベースの復元] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [パーティション &#40;[データベースの復元] ダイアログボックス&#41; &#40;Analysis Services-多次元データ&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services データベースのバックアップと復元](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
