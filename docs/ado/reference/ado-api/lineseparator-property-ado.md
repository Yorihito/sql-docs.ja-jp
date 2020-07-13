---
title: LineSeparator プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9248dcabb4c52ceceb6e4876b034480415e77963
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754819"
---
# <a name="lineseparator-property-ado"></a>LineSeparator プロパティ (ADO)
テキスト[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトの行区切り記号として使用されるバイナリ文字を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **ストリーム**で使用される行区切り文字を示す[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)値を設定または返します。 既定値は**Adcrlf**です。  
  
## <a name="remarks"></a>Remarks  
 **Lineseparator**は、テキスト**ストリーム**の内容を読み取るときに、行を解釈するために使用されます。 [SkipLine](../../../ado/reference/ado-api/skipline-method.md)メソッドでは、行をスキップできます。  
  
 **Lineseparator**は、テキスト**ストリーム**オブジェクトでのみ使用されます ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 **Type**が**adtypebinary**の場合、このプロパティは無視されます。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
