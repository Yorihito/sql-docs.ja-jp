---
title: LEFT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 37f5c1e09464e08932527a667dfc6f8fe306a3ef
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428379"
---
# <a name="left-ssis-expression"></a>LEFT (SSIS 式)
  指定された文字式の一番左の部分から指定された数の文字を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 文字の抽出元となる文字式です。  
  
 *number*  
 返す文字の数を示す整数式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>解説  
 *number* が *character_expression*より長い場合、関数は *character_expression*を返します。  
  
 *number* が 0 の場合、関数は長さが 0 の文字列を返します。  
  
 *number* が負の値の場合、関数はエラーを返します。  
  
 *number* 引数には、変数および列を使用できます。  
  
 LEFT は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LEFT による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。  
  
 引数のいずれかが NULL の場合、LEFT は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 次の例では、文字列リテラルを使用します。 返される結果は `"Mountain"`です。  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>参照  
 [RIGHT (SSIS 式)](right-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
