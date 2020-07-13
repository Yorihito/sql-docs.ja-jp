---
title: キューブ属性のプロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: c02d57e8d24e625dc0613f25d97765c9ae018803
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547044"
---
# <a name="define-cube-attribute-properties"></a>キューブ属性のプロパティの定義
  キューブ属性のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のディメンション属性に一意の設定を指定できます。 次の表では、キューブ属性のプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`AggregationUsage`|集計デザイン ウィザードによる属性の集計の設計方法を指定します。 このプロパティは、以下の値をとります。<br /><br /> `Default`: 既定値。 集計デザイン ウィザードは、属性の種類に基づいて既定のルール (キーの場合は Full、その他の場合は Unrestricted) を適用します。<br /><br /> `None`: キューブの集計にはこの属性を含めないでください。<br /><br /> `Unrestricted`: 集計のデザインウィザードに制限は適用されません。<br /><br /> `Full`: キューブのすべての集計にこの属性が含まれている必要があります。|  
|`AttributeHierarchyEnabled`|属性階層をこのキューブ ディメンションで有効にするかどうかを識別します。 これによって属性階層を特定のキューブまたはディメンション ロールに対して無効にすることができます。 この設定は、基になる属性階層が無効になっている場合には影響を受けません。 既定値は `True` です。|  
|`OptimizedState`|属性階層をこのキューブ ディメンションに対して最適化するかどうかを示します。 これによって属性階層を特定のキューブまたはディメンション ロールに対して最適化できます。 この設定は、基になる属性階層が最適化されていない場合には影響を受けません。 このプロパティは、以下の値をとります。<br /><br /> `FullyOptimized`: 既定値。 インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> `NotOptimized`: インスタンスは追加のインデックスを構築しません。|  
|`AttributeHierarchyVisible`|属性階層をこのキューブ ディメンションで表示するかどうかを示します。 これによって属性階層を特定のキューブまたはディメンション ロールで表示できます。 この設定は、基になる属性階層が表示されていない場合には影響を受けません。 既定値は `True` です。|  
|`AttributeID`|属性の一意識別子 (ID) を示します。|  
  
## <a name="see-also"></a>参照  
 [キューブディメンションのプロパティの定義](define-cube-dimension-properties.md)   
 [キューブ階層のプロパティの定義](define-cube-hierarchy-properties.md)  
  
  
