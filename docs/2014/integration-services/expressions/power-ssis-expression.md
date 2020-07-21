---
title: POWER (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c89408e2d1bd840bc2dac5d7cf27486569f40de
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428299"
---
# <a name="power-ssis-expression"></a>POWER (SSIS 式)
  指定された数値式の結果をべき乗値で返します。 power パラメーターは整数に評価される必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な数値式です。  
  
 *power*  
 有効な数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_R8  
  
## <a name="remarks"></a>解説  
 *numeric_expression* 引数と *power* 引数は、べき乗値の計算前に DT_R8 データ型にキャストされます。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
 *numeric_expression* が 0 に評価され、 *power* が負の値の場合、式エバリュエーターはエラーを返し、返される結果を NULL に設定します。  
  
 *numeric_expression* または *power* の結果が不確定に評価される場合、返される結果は NULL になります。  
  
 *power* 引数には小数を使用できます。 たとえば、power 引数として値 0.5 を使用できます。  
  
## <a name="expression-examples"></a>式の例  
 この例では、数値リテラルを使用しています。 関数は、4 を 3 乗して 64 を返します。  
  
```  
POWER(4,3)  
```  
  
 この例では、 **Length** 列と **DimensionCount** 変数を使用します。 **Length** が 8、 **DimensionCount** が 2 の場合、返される結果は 64 になります。  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>参照  
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
