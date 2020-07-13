---
title: '[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [全般] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c48a07d3b69c3beb0cf05dee29f89b7078658090
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85005790"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a>[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [全般] ページ
  このダイアログ ボックスを使用すると、ポリシー ベースの管理条件を作成または変更できます。 条件とは、ポリシー ベースの管理で管理する対象に許可されている状態のセットをファセットについて指定するブール式です。 **[式]/[フィールド]** ボックスで選択できるプロパティは、使用するファセットによって異なります。 条件と各ファセットおよびポリシーとの関係の詳細については、「 [ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **名前**  
 新しい条件の場合は、新しい条件名を入力します。 既存の条件の場合は、その名前が表示されます。  
  
 **面し**  
 この条件で使用されるファセット。  
  
 **[AndOr]**  
 複数の式を追加する場合は、 **And** または **Or**を使用して式を結合するかどうかを指定します。 式が 1 つだけしかない場合は空白になります。  
  
 **フィールド**  
 各ファセットは、設定可能な 1 つまたは複数のプロパティを公開します。 [フィールド] ボックスで、この条件の式を作成するために使用できるプロパティの一覧からプロパティを選択します。  
  
 **Operator**  
 この式の比較演算子を選択します。 演算子には、=、!=、>、>=、<、<=、[NOT]LIKE、[NOT]IN があります。 プロパティによっては、使用できない演算子もあります。  
  
 **Value**  
 この式の値の設定。 許容値は、ファセットによって異なります。 値は、TRUE/FALSE、文字列、または数値です。 文字列値は、 **'AdventureWorks'** のように、一重引用符で囲む必要があります。 プロパティによっては、使用できない演算子もあります。  
  
## <a name="group-clauses"></a>句のグループ化  
 句をグループ化すると、クエリの他の部分とは別個の、単一のまとまりとして操作できます。これは、数式や論理ステートメントで式の前後をかっこで囲むのと似ています。 句のグループ化は、複雑なクエリを作成するときに役立ちます。  
  
 **句をグループ化するには**  
  
-   Shift キーまたは Ctrl キーを押しながら複数の句をクリックして範囲を選択します。 選択した領域を右クリックし、 **[句のグループ化]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md)  
  
  
