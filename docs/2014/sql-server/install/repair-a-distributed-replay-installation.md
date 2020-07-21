---
title: 分散再生のインストールを修復する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6f8002bfe0f1142cea43704dc88aacb99316eca6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059110"
---
# <a name="repair-a-distributed-replay-installation"></a>分散再生のインストールの修復
  分散再生コンポーネント (コントローラーまたはクライアント) を修復すると、次の処理が行われます。  
  
1.  ディスク上に関連付けられたすべてのファイルを再インストールし、既存のファイルを置き換えます。  
  
2.  対応するサービス アカウントが削除された場合、Windows サービス アカウントを再作成します。  
  
 修復操作を利用してコンポーネントを追加または削除することはできません。 コンポーネントを追加または削除するには、セットアップの [**機能の選択**] ページにある機能ツリーで、対応するコンポーネントをオンまたはオフにし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>分散再生のインストールの失敗を修復するには  
  
1.  [**スタート**] メニューの [**コントロールパネル**] をクリックし、[**プログラムの追加と削除**] をダブルクリックします。  
  
2.  [ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] プログラムの**アンインストールまたは変更**] ウィンドウでを選択し、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ダイアログボックスで [**修復**] をクリックします。  
  
3.  ウィザードの手順に従い、[ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] **機能の選択**] ページで、修復する分散再生コンポーネントを選択し、[**次へ**] をクリックします。  
  
4.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを完了すると、選択した 分散再生の機能が修復されます。  
  
  
