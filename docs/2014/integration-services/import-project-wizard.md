---
title: プロジェクトのインポートウィザード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b9f20115010f2ad51159f29a4b64da195938969
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436649"
---
# <a name="import-project-wizard"></a>プロジェクトのインポート ウィザード
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトのインポート ウィザードを使用すると、既存のプロジェクトに基づいて新しい Integration Services プロジェクトが作成されます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログに既に配置されているプロジェクトをインポートするか、またはプロジェクト配置ファイル (拡張子は .ispac) からプロジェクトをインポートします。  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a>.ispac ファイルまたはカタログ内のプロジェクトに基づいてプロジェクトを作成するには  
  
1.  [**ファイル**]、[**新規作成**] の順にポイントし、[プロジェクト] をクリックします。  
  
2.  **[ビジネス インテリジェンス]** を展開し、 **[Integration Services]** をクリックします。  
  
3.  中央のペインで **[Integration Services インポート ウィザード]** を選択し、ソリューションの **[名前]** 、およびプロジェクトを入力し、プロジェクトの **[フォルダー]** を指定してから **[OK]** をクリックします。  
  
     **Integration Services プロジェクトのインポート ウィザード**が表示されます。 このウィザードを使用すると、既存のプロジェクトに基づいて新しい Integration Services プロジェクトが作成されます。  
  
4.  **[説明]** ページで **[次へ]** をクリックすると、 **[ソースの選択]** ページが表示されます。  
  
5.  .ispac ファイルからプロジェクトをインポートするのか、カタログからプロジェクトをインポートするのかを指定します。  
  
    -   **[プロジェクト配置ファイル]** オプションを選択した場合は、.ispac ファイルのパスを指定します。  
  
    -   **[Integration Services カタログ]** オプションを選択した場合は、カタログが存在するデータベース サーバー インスタンスの名前とカタログ内のプロジェクトのパスを指定します。  
  
6.  **[ソースの選択]** ページで **[次へ]** をクリックすると、 **[確認]** ページが表示されます。 ページに表示される、ウィザードが実行するインポート処理に関する情報を確認します。  
  
7.  **[インポート]** をクリックすると、選択したプロジェクトに基づいて新しい Integration Services プロジェクトが作成されます。  
  
8.  **[結果]** ページに、ウィザードが実行したインポート処理の結果が表示されます。 **[レポートの保存]** をクリックして、レポートを XML ファイルに保存します。  
  
9. [**閉じる**] をクリックしてウィザードを閉じます。  
  
  
