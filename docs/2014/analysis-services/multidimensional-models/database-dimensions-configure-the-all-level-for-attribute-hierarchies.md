---
title: 属性階層の (All) レベルを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9874a8c8a6861bc7d9e44271b089e8af3a4c0ae2
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547174"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a>属性階層の (All) レベルの構成
  では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (All) レベルはシステムによって生成されるオプションのレベルです。 このレベルには 1 つのメンバーが含まれ、その値は直下のレベルに含まれる全メンバーの値の集計です。 このメンバーを All メンバーと呼びます。 All メンバーはシステムによって生成されるメンバーで、ディメンション テーブルには含まれません。 (All) レベルのメンバーは階層の最上位にあるので、このメンバーの値は、階層内の全メンバーの値の集計値です。 通常、All メンバーは階層の既定メンバーとして機能します。  
  
 属性階層に (All) レベルがあるかどうかは属性の `IsAggregatable` プロパティ設定によって決まり、ユーザー定義階層に (All) レベルがあるかどうかはユーザー定義階層の最上位レベルに関する属性の `IsAggregatable` プロパティによって決まります。 `IsAggregatable` プロパティが `True` に設定されている場合は、(All) レベルが存在します。 `IsAggregatable` プロパティが `False` に設定されている場合は、階層に (All) レベルはありません。  
  
## <a name="establishing-the-topmost-level"></a>最上位レベルの設定  
 階層のレベルのソース属性で `IsAggregatable` プロパティが `False` に設定されている場合には、そのレベルより上の階層に集計レベルを表示できません。 非集計レベルは任意の階層の最上位レベルであるか、それより上のレベルのソース属性の `IsAggregatable` プロパティも `False` に設定する必要があります。  
  
## <a name="all-member-and-all-level"></a>All メンバーと (All) レベル  
 (All) レベルの単一のメンバーは、All メンバーと呼ばれます。 ディメンションのプロパティは、 `AttributeAllMemberName` ディメンション内の属性の All メンバーの名前を指定します。 階層の `AllMemberName` プロパティにより、階層の All メンバーの名前が指定されます。  
  
## <a name="see-also"></a>参照  
 [既定のメンバーの定義](attribute-properties-define-a-default-member.md)  
  
  
