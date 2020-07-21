---
title: 変更されたファイルの一覧を表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckinWindow
helpviewer_keywords:
- listing modified files
- modified files list [SQL Server]
- checking in files
ms.assetid: 1b053719-8500-4300-a169-fffca5801dd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9f500eb460cab8734a062ddf6561cbdf01d0f773
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927573"
---
# <a name="view-a-list-of-modified-files"></a>変更されたファイルの一覧表示
  [**保留中のチェックイン**] ウィンドウを使用すると、現在のソリューションでチェックアウトされているファイルの一覧を常に表示したり、1回のボタンクリックでこれらのファイルをチェックインしたりできます。  
  
### <a name="to-view-a-list-of-modified-files"></a>変更されたファイルの一覧を表示するには  
  
1.  [**表示**] メニューの [**保留中のチェックイン**] をクリックします。  
  
2.  選択したファイルをチェックインするには、[**チェックイン**] をクリックします。 または、[**保留中のチェックイン**] ウィンドウを環境の右側にドッキングして、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 作業が終了したときにファイルをチェックインできるようにすることもできます。  
  
     **チェックイン**  
     ソリューションにチェックインします。  
  
     **コメント**  
     プレーンテキスト コメントを保留中のチェックインに関連付けます。 コメントが作成され、プロジェクトの各バージョンに関連付けられ、ソース管理データベースに格納されます。  
  
     **Options**  
     [**チェックイン**] ボタンをクリックしたときにソース管理で実行するアクションを指定します。  
  
    -   **[すべてのチェックアウト状態を保持]**  
  
         ファイルをチェックアウトした状態のままで、変更がソース管理プロバイダーに書き込まれるように指定します。  
  
     **並べ替え**  
     アイテムの一覧に表示された列の並べ替え順序を指定します。  
  
     **[列]**  
     ウィンドウのアイテムの一覧に追加できる列の一覧を表示します。  
  
     **ツリー ビュー**  
     チェックインするソリューションまたはプロジェクトのフォルダーおよびファイルの階層を表示します。  
  
     **[平面表示]**  
     ソース管理接続の下にあるフラットリストとしてチェックインしているファイルを表示します。  
  
     **[バージョンの比較]**  
     [Visual SourceSafe の**相違点のオプション**] ダイアログボックスを開きます。このダイアログボックスでは、開発環境プロジェクト内の選択したファイルを選択した他のファイルと比較し、相違がある場合はその相違点を表示します。  
  
     **チェックアウトを元に戻す**  
     [**保留中のチェックイン**] ウィンドウで選択したすべての項目のチェックアウトを元に戻します。  
  
     **名前**  
     チェックインに利用可能なアイテムの一覧を表示します。 項目の横に、オン状態のチェック ボックスが表示されます。 チェックインしないアイテムがある場合は、対象アイテムの横のチェック ボックスをオフにしてください。  
  
## <a name="see-also"></a>参照  
 [チェックインの管理](../../2014/database-engine/manage-checkins.md)   
 [チェックアウトの管理](../../2014/database-engine/manage-checkouts.md)  
  
  
