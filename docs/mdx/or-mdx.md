---
title: OR (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45063e9f2aca6a924289d4d52434535d16c9a08e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68055711"
---
# <a name="or-mdx"></a>OR (MDX)


  2つの数値式の論理和を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>パラメーター  
 Expression1  
 数値を返す有効な多次元式 (MDX) 式です。  
  
 Expression2  
 数値を返す有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 いずれかまたは両方の引数が**true**に評価される場合に**True**を返すブール値です。それ以外の場合は**false**。  
  
## <a name="remarks"></a>Remarks  
 **Or**演算子は、演算子が論理和を実行する前に、両方の引数をブール値 (0 の場合は**false**、それ以外の場合は**true**) として処理します。 次の表は、 **or**演算子が論理和をどのように実行するかを示しています。  
  
|*Expression1*|*Expression2*|戻り値|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>例  
 次のクエリには、Customer ディメンションの性別階層の現在のメンバーが男性であるか、Customer ディメンションの配偶の状態階層の現在のメンバーが既婚である場合に、文字列 "既婚 OR 男性" を返す計算されるメジャーが含まれています。それ以外の場合は、文字列 "UNMARRIED OR 女性" を返します。  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
