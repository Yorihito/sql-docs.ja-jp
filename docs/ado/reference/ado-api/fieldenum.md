---
description: FieldEnum
title: '|Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
author: rothja
ms.author: jroth
ms.openlocfilehash: b562d480cfbebefdee82703e0c953854de07d064
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443744"
---
# <a name="fieldenum"></a>FieldEnum
[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトの[fields](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションで参照される特殊なフィールドを指定します。  
  
## <a name="remarks"></a>解説  
 これらの定数は、 **レコード**に関連付けられている特殊なフィールドにアクセスするための "ショートカット" を提供します。 **フィールドコレクションから**[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトを取得し、**フィールド**オブジェクトの[Value](../../../ado/reference/ado-api/value-property-ado.md)プロパティを使用してその内容を取得します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|**レコード**に関連付けられている既定の[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトを格納しているフィールドを参照します。|  
|**adRecordURL**|-2|現在の **レコード**の絶対 URL 文字列を含むフィールドを参照します。|
