---
title: 8060(DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2d75bd4a1d4b75d9acb153c3a3aec9efcf58d876
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669744"
---
# <a name="divide-dmx"></a>(除算) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1つの数値を別の数値で除算する算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>パラメーター  
 *被除数*  
 数値を返す有効なデータマイニング拡張機能 (DMX) 式です。  
  
 *公約数*  
 数値を返す有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>Remarks  
 この演算子が返す値は、最初の式が2番目の式で除算した商を表します。  
  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 除算の結果が NULL 値になる場合、演算子はエラーになります。 除数と被除数の両方が null 値に評価される場合、演算子は null 値を返します。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;算術演算子](../dmx/operators-arithmetic.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)   
 [&#40;SSIS 式&#41;の分割](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;&#41; &#40;Transact-sql&#41;の分割](../t-sql/language-elements/divide-transact-sql.md)  
  
  
