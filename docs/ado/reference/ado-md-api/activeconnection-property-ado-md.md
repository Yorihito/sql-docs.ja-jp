---
title: ActiveConnection プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 13a24320f7b49d8d2a0e1341bff2d9a4cca575dd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765323"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection プロパティ (ADO MD)
現在のセルセットまたはカタログが現在どの ADO[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトに属しているかを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 接続または**接続**オブジェクトを定義する文字列を含む**Variant**を設定します。値の取得もできます。 既定値は空です。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは、有効な ADO**接続**オブジェクトまたは有効な接続文字列に設定できます。 このプロパティが接続文字列に設定されている場合、プロバイダーはこの定義を使用して新しい**接続**オブジェクトを作成し、接続を開きます。  
  
 [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md)メソッドの*ActiveConnection*引数を使用して[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトを開くと、 **ActiveConnection**プロパティは引数の値を継承します。  
  
 [Catalog](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)オブジェクトの**ActiveConnection**プロパティを**Nothing**に設定すると、関連付けられているデータ[(cubedefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)コレクション内のデータ、関連する[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)、[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクトなど) が解放されます。 **カタログ**を開くために使用された**接続**オブジェクトを閉じると、 **ActiveConnection**プロパティを**Nothing**に設定した場合と同じ効果があります。  
  
 **カタログ**オブジェクトの**ActiveConnection**プロパティによって参照される接続の既定のデータベースを変更すると、**カタログ**の内容が無効になります。  
  
 開いている**セルセット**オブジェクトの**ActiveConnection**プロパティを変更しようとすると、エラーが発生します。  
  
> [!NOTE]
>  Visual Basic では、 **ActiveConnection**プロパティを**接続**オブジェクトに設定するときに、 **Set**キーワードを使用することを忘れないでください。 **Set**キーワードを省略した場合、実際には、**接続**オブジェクトの既定のプロパティ**ConnectionString**に等しい**ActiveConnection**プロパティを設定します。 コードは正常に動作します。ただし、データソースへの追加の接続を作成すると、パフォーマンスに悪影響を及ぼす可能性があります。  
  
 MSOLAP データプロバイダーを使用する場合は、接続文字列のデータソースをサーバー名に設定し、初期カタログをデータソースのカタログの名前に設定します。 サーバーから切断されているキューブファイルに接続するには、場所をへの完全パスに設定します。.CUB ファイル。 どちらの場合も、プロバイダーをプロバイダー名に設定します。 たとえば、次の文字列は MSOLAP プロバイダーを使用して、 **Servername**という名前のサーバー上にある Bobs ビデオストアという名前のカタログに接続します。  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 次の文字列は、C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub 場所にあるローカルのキューブファイルに接続します。  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Catalog オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>参照  
 [セルセットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open メソッド (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
