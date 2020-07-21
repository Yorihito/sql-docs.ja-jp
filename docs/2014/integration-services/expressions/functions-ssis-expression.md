---
title: 関数 (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2023cccadefaf3274a7032fe188b7d887a23b3d0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428659"
---
# <a name="functions-ssis-expression"></a>関数 (SSIS 式)
  式言語には、式で使用するための関数セットが含まれています。 式で 1 つの関数を使用することもできますが、通常、式は関数と演算子を組み合わせて使用したり、複数の関数を使用します。  
  
 関数は、次の各グループに分類されます。  
  
-   数学関数。パラメーターとして渡された数値型の入力値に基づいて計算を実行し、数値を返します。  
  
-   文字列関数。文字列型または 16 進数の入力値に対して操作を実行し、文字列値または数値を返します。  
  
-   日付関数および時刻関数。日時の値に対して操作を実行し、文字列、数値、または日時の値を返します。  
  
-   システム関数。式に関する情報を返します。  
  
 式言語には、次の数学関数が用意されています。  
  
|Function|説明|  
|--------------|-----------------|  
|[ABS &#40;SSIS 式&#41;](abs-ssis-expression.md)|数値式の正の絶対値を返します。|  
|[EXP &#40;SSIS 式&#41;](exp-ssis-expression.md)|指定した式の e を基数とする指数を返します。|  
|[CEILING &#40;SSIS 式&#41;](ceiling-ssis-expression.md)|数値式以上で最小の整数値を返します。|  
|[FLOOR &#40;SSIS 式&#41;](floor-ssis-expression.md)|数値式以下で最大の整数を返します。|  
|[LN &#40;SSIS 式&#41;](ln-ssis-expression.md)|数値式の自然対数を返します。|  
|[LOG &#40;SSIS 式&#41;](log-ssis-expression.md)|数値式の常用対数を返します。|  
|[POWER &#40;SSIS 式&#41;](power-ssis-expression.md)|指定された数値式の結果をべき乗値で返します。|  
|[ROUND &#40;SSIS 式&#41;](round-ssis-expression.md)|指定された長さまたは有効桁数に丸めた数値式を返します。 。|  
|[SIGN &#40;SSIS 式&#41;](sign-ssis-expression.md)|数値式の符号として正 (+)、負 (-)、ゼロ (0) のいずれかを返します。|  
|[SQUARE &#40;SSIS 式&#41;](square-ssis-expression.md)|数値式の 2 乗値を返します。|  
|[SQRT &#40;SSIS 式&#41;](sqrt-ssis-expression.md)|数値式の平方根を返します。|  
  
 式エバリュエーターには、次の文字列関数が用意されています。  
  
|Function|説明|  
|--------------|-----------------|  
|[CODEPOINT &#40;SSIS 式&#41;](codepoint-ssis-expression.md)|文字式の左端の文字の Unicode コード値を返します。|  
|[FINDSTRING &#40;SSIS 式&#41;](findstring-ssis-expression.md)|文字式内のある文字列が指定回数目に検出された場所を、1 を基点とするインデックスで返します。|  
|[HEX &#40;SSIS 式&#41;](hex-ssis-expression.md)|整数の 16 進値を表す文字列を返します。|  
|[LEN &#40;SSIS 式&#41;](len-ssis-expression.md)|文字式の文字数を返します。|  
|[LEFT &#40;SSIS 式&#41;](left-ssis-expression.md)|指定された文字式の一番左の部分から指定された数の文字を返します。|  
|[LOWER &#40;SSIS 式&#41;](lower-ssis-expression.md)|大文字が小文字に変換された状態の文字式を返します。|  
|[LTRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)|先頭のスペースを削除した後の文字式を返します。|  
|[REPLACE &#40;SSIS &#41;](replace-ssis-expression.md)|式に含まれている文字列を別の文字列または空の文字列で置き換えた文字式を返します。|  
|[REPLICATE &#40;SSIS 式&#41;](replicate-ssis-expression.md)|指定された回数だけレプリケートされた文字式を返します。|  
|[REVERSE &#40;SSIS 式&#41;](reverse-ssis-expression.md)|文字式を逆に並べ替えたものを返します。|  
|[RIGHT &#40;SSIS 式&#41;](right-ssis-expression.md)|指定された文字式の一番右の部分から指定された数の文字を返します。|  
|[RTRIM &#40;SSIS 式&#41;](rtrim-ssis-expression.md)|末尾のスペースを削除した後の文字式を返します。|  
|[SUBSTRING &#40;SSIS 式&#41;](substring-ssis-expression.md)|文字式の一部を返します。|  
|[TRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)|先頭および末尾のスペースを削除した後の文字式を返します。|  
|[UPPER &#40;SSIS 式&#41;](upper-ssis-expression.md)|小文字が大文字に変換された状態の文字式を返します。|  
  
 式エバリュエーターには、次の日付と時刻関数が用意されています。  
  
|Function|説明|  
|--------------|-----------------|  
|[DATEADD (SSIS 式)](dateadd-ssis-expression.md)|指定された日付に日付または期間を加えて、新しい DT_DBTIMESTAMP 値を返します。|  
|[DATEDIFF (SSIS 式)](datediff-ssis-expression.md)|指定された 2 つの日付間の差を、日付および時刻の単位で返します。|  
|[DATEPART (SSIS 式)](datepart-ssis-expression.md)|ある日付の、特定の日付要素を整数で返します。|  
|[DAY (SSIS 式)](day-ssis-expression.md)|指定された日付の日を整数で返します。|  
|[GETDATE (SSIS 式)](getdate-ssis-expression.md)|システムの現在の日付を返します。|  
|[GETUTCDATE (SSIS 式)](getutcdate-ssis-expression.md)|システムの現在の日付を UTC 時刻 (協定世界時またはグリニッジ標準時) で返します。|  
|[MONTH (SSIS 式)](month-ssis-expression.md)|指定された日付の月を表す整数を返します。|  
|[YEAR (SSIS 式)](year-ssis-expression.md)|指定された日付の年を表す整数を返します。|  
  
 式エバリュエーターには、次の NULL 関数が用意されています。  
  
|Function|説明|  
|--------------|-----------------|  
|[ISNULL &#40;SSIS 式&#41;](null-ssis-expression.md)|式が NULL かどうかに基づいてブール型の結果を返します。|  
|[NULL &#40;SSIS 式&#41;](null-ssis-expression.md)|要求されたデータ型の NULL 値を返します。|  
  
 式の名前は大文字で表示されますが、大文字と小文字は区別されません。 たとえば、"null" は "NULL" を使用した場合と同様に機能します。  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;SSIS 式&#41;](operators-ssis-expression.md)   
 [Integration Services 式の詳細の例](examples-of-advanced-integration-services-expressions.md)   
 [Integration Services &#40;SSIS&#41; 式](integration-services-ssis-expressions.md)  
  
  
