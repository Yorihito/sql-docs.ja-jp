---
title: StayInSync Property |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
author: rothja
ms.author: jroth
ms.openlocfilehash: f36eace18280cd810341c5eeeec1fb294999e6ec
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759638"
---
# <a name="stayinsync-property"></a>StayInSync プロパティ
親の行位置が変更されたときに、基になる子レコード (つまり、*チャプター*) への参照が変更されるかどうかを階層[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトで示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **ブール**値を設定または返します。 既定値は **True** です。 **True**の場合、親の**Recordset**オブジェクトが行の位置を変更すると、チャプターが更新されます。**False**の場合、親の**Recordset**オブジェクトが行の位置を変更した場合でも、チャプターは前の章のデータを参照し続けます。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは、 [OLE DB 用の Microsoft データ整形サービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)によってサポートされるレコードセットなどの階層的なレコードセットに適用されます。子**レコード**セットを取得する前に、親**レコード**セットに設定する必要があります。 このプロパティは、階層的なレコードセットの移動を簡略化します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [StayInSync プロパティの例 (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [OLE DB 用の Microsoft データ整形サービス (ADO サービスプロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
