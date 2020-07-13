---
title: ディメンションの順序を定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd5ea148e374c18c530ba0a15c80dbb23983020
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544584"
---
# <a name="define-the-ordering-for-a-dimension"></a>ディメンションの順序の定義
  キューブまたはディメンションに属性の順序指定の拡張機能を追加して、属性のメンバーの順序付け方法を指定します。 メンバーは、属性の名前またはキー、あるいは、属性リレーションシップに基づいた別の属性の名前またはキーによって順序を指定できます。 既定では、名前によってメンバーの順序を指定します。 この拡張機能により、ディメンション内にある属性の `OrderBy` および `OrderByAttributeID` プロパティ設定が変更されます。  
  
 属性の順序を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[属性の順序の指定]** オプションを選択します。 このウィザードでは、属性の順序の適用先となるディメンションを選択し、選択したディメンションの属性の順序付け方法を指定する手順が示されます。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[属性の順序の指定]** ページで、属性の順序の適用先になるディメンションを指定します。 選択したこのディメンションに追加された属性の順序指定の拡張機能により、ディメンションが変更されます。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="specifying-ordering"></a>順序の指定  
 **[属性の順序の指定]** の 2 ページ目で、ディメンションのすべての属性を順序付ける方法を指定します。  
  
 **[属性の並べ替え]** 列で、順序付けに使用する属性を変更できます。 メンバーの順序付けに使用する属性が一覧にない場合は、一覧を下にスクロールして [ **\<New attribute...>** **列の選択**] ダイアログボックスを開くと、ディメンションテーブルの列を選択できます。 **[列の選択]** ダイアログ ボックスを使用して列を選択すると、属性のメンバーを順序付ける追加の属性が作成されます。  
  
 **[条件]** 列で、 **[キー]** または **[名前]** のどちらによって属性のメンバーを順序付けるかを選択できます。  
  
  
