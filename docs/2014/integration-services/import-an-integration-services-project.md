---
title: Integration Services のプロジェクトのインポート |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af91900ce22ecd3d42a8d83557e1780e30c5ca73
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436849"
---
# <a name="import-an-integration-services-project"></a>Integration Services プロジェクトのインポート
  既存の配置ファイル (.ispac) または Integration Services カタログに配置されたプロジェクトからプロジェクトを作成するには、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の**プロジェクトのインポート ウィザード**を使用します。 この機能は、プロジェクトの元のコピーがない状態で、.ispac ファイルまたは SSISDB カタログからプロジェクトを作成する場合に、特に便利です。  
  
### <a name="to-import-a-project"></a>プロジェクトをインポートするには  
  
1.  で、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [ **New**  >  **ファイル**] メニューの [新しい**プロジェクト**] をクリックします。  
  
2.  **[新しいプロジェクト]** ウィンドウの **[インストールされているテンプレート]** 領域で **[ビジネス インテリジェンス]** を展開し、 **[Integration Services]** をクリックします。  
  
3.  プロジェクトの種類の一覧から **Integration Services プロジェクトのインポート ウィザード** をクリックします。  
  
4.  作成する新しいプロジェクトの名前を、 **[名前]** ボックスに入力します。  
  
5.  プロジェクトのパスまたは場所を **[場所]** ボックスに入力するか、または **[参照]** をクリックして選択します。  
  
6.  **[ソリューション名]** ボックスにソリューションの名前を入力します。  
  
7.  **[OK]** をクリックして **[Integration Services プロジェクトのインポート ウィザード]** ダイアログ ボックスを起動します。  
  
8.  **[次へ]** をクリックして、 **[ソースの選択]** ページに移動します。  
  
9. **.ispac** ファイルからインポートする場合は、ファイル名を含むパスを **[パス]** ボックスに入力します。 **[参照]** をクリックして、ソリューションを格納するフォルダーに移動し、 **[ファイル名]** ボックスにファイル名を入力して、 **[開く]** をクリックします。  
  
     **Integration Services カタログ**からインポートする場合は、データベース インスタンス名を **[サーバー名]** ボックスに入力するか、または **[参照]** をクリックしてカタログを含むデータベース インスタンスを選択します。  
  
     **[パス]** ボックスの横にある **[参照]** をクリックし、カタログのフォルダーを展開して、インポートするプロジェクトを選択し、 **[OK]** をクリックします。  
  
     **[次へ]** をクリックして **[確認]** ページに移動します。  
  
10. 情報を確認し、 **[インポート]** をクリックして、選択した既存のプロジェクトに基づくプロジェクトを作成します。  
  
11. 省略可能: **[レポートの保存]** をクリックして、結果をファイルに保存します  
  
12. **[閉じる]** をクリックして **[Integration Services プロジェクトのインポート ウィザード]** ダイアログ ボックスを閉じます。  
  
  
