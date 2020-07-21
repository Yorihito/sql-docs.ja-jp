---
title: Fields コレクション (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
author: rothja
ms.author: jroth
ms.openlocfilehash: ecf6d672bd82b6ac532306cd1ca6fc2400b215e8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762563"
---
# <a name="fields-collection-ado"></a>Fields コレクション (ADO)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)または[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトのすべての[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトを格納します。  
  
## <a name="remarks"></a>解説  
 **レコードセット**オブジェクトには、 **Field**オブジェクトで構成された**フィールド**コレクションがあります。 各**Field**オブジェクトは、**レコードセット**内の列に対応します。 コレクションの[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを呼び出すことによって、**レコードセット**を開く前に**フィールド**コレクションを設定できます。  
  
> [!NOTE]
>  **Field**オブジェクトの使用方法の詳細については、「 **field**オブジェクト」を参照してください。  
  
 **Fields**コレクションには、仮メソッドがあります。[このメソッドは](../../../ado/reference/ado-api/append-method-ado.md)、**フィールド**オブジェクトを作成し、コレクションに追加し、 **Update**メソッドを使用して、追加または削除を終了します。  
  
 **レコード**オブジェクトには、2つの特殊なフィールドがあります。これらのフィールドには、定数定数を使用[してインデックス](../../../ado/reference/ado-api/fieldenum.md)を作成できます。 一方の定数は、**レコード**の既定のストリームを格納しているフィールドにアクセスします。もう1つの定数は、**レコード**の絶対 URL 文字列を含むフィールドにアクセスします。  
  
 特定のプロバイダー (たとえば、 [Microsoft OLE DB Provider For Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) では、**レコード**または**レコードセット**に使用できるフィールドのサブセットを**フィールド**コレクションに設定できます。 その他のフィールドは、名前によって最初に参照されるか、コードによってインデックスが作成されるまで、コレクションに追加されません。  
  
 存在しないフィールドを名前で参照しようとすると、 **Adfieldpendinginsert**という[状態](../../../ado/reference/ado-api/status-property-ado-field.md)の**フィールドコレクションに**新しい**フィールド**オブジェクトが追加されます。 [Update](../../../ado/reference/ado-api/update-method.md)を呼び出すと、プロバイダーで許可されている場合、ADO によってデータソースに新しいフィールドが作成されます。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Fields コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)
