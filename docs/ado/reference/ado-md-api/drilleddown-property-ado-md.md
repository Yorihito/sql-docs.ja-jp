---
title: Drilの Down プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
author: rothja
ms.author: jroth
ms.openlocfilehash: c5819609f06b37ffad08918968530b66df169c64
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764263"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown プロパティ (ADO MD)
子が軸上の[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)の直後にあるかどうかを示します。  
  
## <a name="return-values"></a>戻り値  
 **ブール**値を返し、読み取り専用です。 **Drilleddown**は、現在のメンバーの子メンバーが軸に存在しない場合に**True**を返します。 現在のメンバーが軸上に1つ以上の子メンバーを持っている場合、 **Drilleddown**は**False**を返します。  
  
## <a name="remarks"></a>Remarks  
 このメンバーの直後にある軸にこのメンバーの子が少なくとも1つあるかどうかを確認するには、 **Drilの下**のプロパティを使用します。 この情報は、メンバーを表示するときに役立ちます。  
  
 このプロパティは、 [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクトに属する[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクトでのみサポートされます。 このプロパティが[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクトに属している**メンバー**オブジェクトから参照されている場合に、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [ParentSameAsPrev プロパティ (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
