---
title: ディメンションへのカスタム集計の追加 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed843b8b0005ff62f05b13ebd20024d528857388
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544608"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a>ディメンションへのカスタム集計の追加
  カスタム集計拡張機能をキューブまたはディメンションに追加して、ディメンション メンバーに関連付けられている既定の集計を、別の単項演算子に置き換えます。 この拡張機能では、親子階層内のメンバーのロールアップを定義する単項演算子列がディメンション テーブルに指定されます。 単項演算子は、親子階層内の親属性に適用されます。  
  
> [!NOTE]  
>  カスタム集計は、既存のデータ ソースを基にしたディメンションにのみ使用できます。 データ ソースを使用せずに作成されたディメンションに対しては、スキーマ生成ウィザードを実行し、データ ソース ビューを作成してからカスタム集計を追加する必要があります。  
  
 カスタム集計を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページで **[単項演算子の指定]** オプションを選択します。 次に、このウィザードでは、カスタム集計の適用先のディメンションを選択し、カスタム集計を識別する手順を示します。  
  
> [!NOTE]  
>  ビジネス インテリジェンス ウィザードを実行してカスタム集計を追加する前に、拡張するディメンションに親子属性階層が含まれていることを確認してください。 詳細については、「[親子階層](parent-child-dimension.md)」を参照してください。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[単項演算子の指定]** ページで、カスタム集計の適用先のディメンションを指定します。 この選択したディメンションに追加されるカスタム集計が、ディメンションへの変更内容になります。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="adding-custom-aggregation-unary-operator"></a>カスタム集計 (単項演算子) の追加  
 **[単項演算子の指定]** の次のページで、カスタム集計の親属性と、単項演算子のディメンション テーブル内の基になる列を指定します。 **親属性**は、プロパティがに設定されている属性を一覧表示 `Usage` `Parent` します。 複数の親属性が存在する場合は、使用する親子リレーションシップに対応する親属性を選択します。 親属性が一覧に含まれていない場合、ディメンションには有効な親子階層が存在していません。  
  
 **[基になる列]** で、単項演算子を含む文字列の列を選択します (この選択によって、親属性のプロパティが設定さ `UnaryOperatorColumn` れます)。ディメンションテーブルには、単項ロールアップ演算子を指定する文字列列も必要です。 この列の文字列値には、有効な集計演算子が含まれている必要があります。 行が空の場合は、対応するメンバーが普通に計算されます。 列の式が有効でない場合は、そのメンバーを使用するセル値が取得されたときに実行時エラーが発生します。 詳細については、 [「親子ディメンションの単項演算子」](parent-child-dimension-attributes-unary-operators.md)を参照してください。  
  
  
