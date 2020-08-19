---
description: Close メソッド (ADO MD)
title: Close メソッド (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a0cff50bbbb238febdf5f187e6bf99cf88a4762
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441174"
---
# <a name="close-method-ado-md"></a>Close メソッド (ADO MD)
開いているセルセットを閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>解説  
 **Close**メソッドを使用して[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトを閉じると、関連する[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)、[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)、[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)、または[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクトのデータを含む、関連付けられたデータが解放されます。 **セルセット**を閉じると、メモリからは削除されません。プロパティの設定を変更し、後でもう一度開くことができます。 メモリからオブジェクトを完全に削除するには、オブジェクト変数を **Nothing**に設定します。  
  
 後で [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) メソッドを呼び出して、同じまたは別のソース文字列を使用して **セルセット** を再び開くことができます。 **Cellset**オブジェクトが閉じられている間に、プロパティを取得したり、基になるデータまたはメタデータを参照するメソッドを呼び出したりすると、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Axis オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Cell オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Open メソッド (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Position オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
