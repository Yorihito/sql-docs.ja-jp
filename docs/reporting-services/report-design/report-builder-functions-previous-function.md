---
title: Previous 関数 (レポート ビルダー) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 882a098aaabcd4610fc6623e9741f7eeaa4f53ec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081182"
---
# <a name="report-builder-functions---previous-function"></a>レポート ビルダー関数 - Previous 関数
  アイテムの、指定されたスコープ内の直前のインスタンスに対応する値または指定された集計値を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *式 (expression)*  
 (**Variant** または **Binary**) データを識別し、直前の値を取得するための式 ( `Fields!Fieldname.Value` や `Sum(Fields!Fieldname.Value)`など) です。  
  
 *スコープ (scope)*  
 (**文字列**) 省略可。 **expression** で指定された直前の値を取得する対象となるスコープを示すグループやデータ領域の名前、または NULL ( [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]では *Nothing*) です。  
  
## <a name="return-type"></a>戻り値の型  
 **Variant** または **Binary**を返します。  
  
## <a name="remarks"></a>解説  
 **Previous** 関数は、すべての並べ替えおよびフィルター処理が適用された後、指定されたスコープで評価された式の直前の値を返します。  
  
 *expression* に集計が含まれていない場合、 **Previous** 関数では、レポート アイテムの現在のスコープが既定になります。  
  
 詳細グループで、直前の詳細行のフィールド参照の値を指定するには **Previous** を使用します。  
  
> [!NOTE]  
>  **Previous** 関数では、詳細グループでのみフィールド参照がサポートされます。 たとえば、詳細グループのテキスト ボックスの場合、 `=Previous(Fields!Quantity.Value)` では、直前の行から `Quantity` フィールドのデータが返されます。 この式が先頭行にある場合は、NULL (**では** Nothing [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) が返されます。  
  
 既定のスコープを使用する集計関数が *expression* に含まれている場合、 **Previous** では、集計関数の呼び出しで指定されたスコープの直前のインスタンス内のデータを集計します。  
  
 既定以外のスコープを指定する集計関数が *expression* に含まれている場合、 *Previous* 関数の **scope** パラメーターには、集計関数の呼び出しで指定されたスコープのコンテナー スコープを指定する必要があります。  
  
 関数 **Level**、 **InScope**、 **Aggregate** 、 **Previous** は、 *expression*パラメーターで使用できません。 集計関数に *recursive* パラメーターを指定することはサポートされていません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="examples"></a>例  
  
### <a name="description"></a>説明  
 次のコード例は、データ領域の既定のデータ行に配置されると、直前の行の `LineTotal` フィールドの値が表示されます。  
  
### <a name="code"></a>コード  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>説明  
 次の例では、特定の月日の売上合計と、前年のその月日の値を計算する式を示します。 この式は、子グループ `GroupbyDay`に属する行内のセルに追加されます。 その親グループは `GroupbyMonth`で、このグループの親グループは `GroupbyYear`です。 この式では、GroupbyDay (既定のスコープ) の結果、次に `GroupbyYear` (親グループ `GroupbyMonth`の親) の結果が表示されます。  
  
 たとえば、親グループが `Year`、その子グループが `Month`、そのまた子グループが `Day` という名前のデータ領域 (入れ子レベル 3) の場合、 グループ `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` に関連付けられた行内の式 `Day` は、前年の同じ月日の売上高の値を返します。  
  
### <a name="code"></a>コード  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
