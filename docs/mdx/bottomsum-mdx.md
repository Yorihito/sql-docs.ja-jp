---
title: BottomSum (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e49fc5a7ffd4c0adff38628a143ded695785e29
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016894"
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)


  指定されたセットを昇順で並べ替え、合計が指定した値以下である最小値を持つ組のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *[値]*  
 各組の比較対象となる値を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **BottomSum**関数は、指定されたセットに対して評価される指定されたメジャーの合計を計算し、セットを昇順に並べ替えます。 次に、関数は、指定された数値式の合計が指定された値 (sum) 以上である、最小値を持つ要素を返します。 この関数は、累積合計が指定値以上になるセットの最小サブセットを返します。 返される要素は、最小値から最大値に順に並べ替えられます。  
  
> [!IMPORTANT]  
>  **BottomSum**関数は、 [TopSum](../mdx/topsum-mdx.md)関数と同様に、常に階層を解除します。  
  
## <a name="examples"></a>使用例  
 次の例では、自転車カテゴリの場合、2003会計年度の Geography ディメンションの Geography 階層にある City レベルの最小のメンバーのセットが返されます。また、販売店の Sales Amount メジャーを使用している累積合計は、少なくとも5万の合計になります (このセットのメンバーのうち、最も少ない売り上げの数)。  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
