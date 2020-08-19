---
description: Source プロパティ (ADO Record)
title: Source プロパティ (ADO Record) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f8fb7ece2d2046706df91814b2d098e0a900d18
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442044"
---
# <a name="source-property-ado-record"></a>Source プロパティ (ADO Record)
[レコード](../../../ado/reference/ado-api/record-object-ado.md)によって表されるデータソースまたはオブジェクトを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **レコード**によって表されるエンティティを示す**バリアント**値を設定または返します。  
  
## <a name="remarks"></a>解説  
 **Source**プロパティは、 **Record**オブジェクト[Open](../../../ado/reference/ado-api/open-method-ado-record.md)メソッドの*source*引数を返します。 絶対 URL または相対 URL 文字列を含めることができます。 絶対 URL を使用する場合は、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) プロパティを設定しなくても **レコード** オブジェクトを直接開くことができます。 この場合、暗黙的な **接続** オブジェクトが作成されます。  
  
 **ソース**プロパティには、既に開いている**レコードセット**への参照を含めることもできます。これにより、レコード**セット**の現在の行を表す**Record**オブジェクトが開きます。  
  
 **Source**プロパティには、プロバイダーから1行のデータを返す[Command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトへの参照を含めることもできます。  
  
 **ActiveConnection**プロパティも設定されている場合、 **Source**プロパティはその接続のスコープ内に存在するいくつかのオブジェクトを指す必要があります。 たとえば、ツリー構造の名前空間では、 **ソース** プロパティに絶対 url が含まれている場合、接続文字列の url で識別されるノードのスコープ内に存在するノードを指す必要があります。 **ソース**プロパティに相対 URL が含まれている場合は、 **ActiveConnection**プロパティによって設定されたコンテキスト内で検証されます。  
  
 **Record オブジェクト**が閉じている間、 **Source**プロパティは読み取り/書き込み可能であり、**レコード**オブジェクトが開いている間は読み取り専用になります。  
  
> [!NOTE]
>  Http スキームを使用する Url は、 [インターネット公開のために Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)を自動的に呼び出します。 詳細については、「 [絶対 url と相対 url](../../../ado/guide/data/absolute-and-relative-urls.md)」を参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Source プロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Source プロパティ (ADO Recordset)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
