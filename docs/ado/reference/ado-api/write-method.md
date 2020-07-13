---
title: Write メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 911a9dfb21c054dc95c54d9fb429d628d8e01fa4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764433"
---
# <a name="write-method"></a>Write メソッド
バイナリデータを[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトに書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Buffer*  
 書き込むバイト配列を格納している**Variant** 。  
  
## <a name="remarks"></a>Remarks  
 指定されたバイトは、各バイト間にスペースを入れずに**ストリーム**オブジェクトに書き込まれます。  
  
 現在の[位置](../../../ado/reference/ado-api/position-property-ado.md)は、書き込まれたデータに続くバイトに設定されます。 **Write**メソッドは、ストリーム内の残りのデータを切り捨てません。 これらのバイトを切り捨てる場合は、 [SetEOS](../../../ado/reference/ado-api/seteos-method.md)を呼び出します。  
  
 現在の[EOS](../../../ado/reference/ado-api/eos-property.md)位置を超えて書き込む場合、**ストリーム**の[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)は新しいバイト数を含むように増加し、 **EOS**は**ストリーム**の新しい最後のバイトに移動します。  
  
> [!NOTE]
>  **Write**メソッドはバイナリストリームで使用されます ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adtypebinary**です)。 テキストストリーム (**型**は**adTypeText**) の場合は、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)を使用します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
