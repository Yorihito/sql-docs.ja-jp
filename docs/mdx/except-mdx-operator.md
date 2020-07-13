---
title: '- ば(MDX) |Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cf0121d1be3cd2943a801f3c72ca4952b70ec681
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139080"
---
# <a name="except-mdx-operator"></a>Except (MDX) 演算子


  2 つのセットの重複メンバーを削除して差集合を返すセット演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression - Set_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 指定した両方のパラメーターによって共有されていないメンバーを含むセットです。  
  
## <a name="remarks"></a>Remarks  
 **-(Except)** 演算子は機能的には[Except](../mdx/except-mdx-function.md)関数と同等です。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を次に示します。  
  
```  
// This query shows the quantity of orders for all product categories  
// with the exception of Components.  
SELECT   
   [Measures].[Order Quantity] ON COLUMNS,  
   [Product].[Product Categories].[All].Children   
   - [Product].[Product Categories].[Components] ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
