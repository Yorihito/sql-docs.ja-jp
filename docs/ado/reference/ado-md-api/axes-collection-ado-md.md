---
description: Axes コレクション (ADO MD)
title: Axes コレクション (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Axes
- Cellset::Axes
helpviewer_keywords:
- Axes collection [ADO MD]
ms.assetid: 072fb21a-ec0f-4b02-9022-1cef3ad4bfff
author: rothja
ms.author: jroth
ms.openlocfilehash: cc93e9ea8568a535067addbd51258074945200db
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441320"
---
# <a name="axes-collection-ado-md"></a>Axes コレクション (ADO MD)
セルセットを定義する [軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md) オブジェクトを格納します。  
  
## <a name="remarks"></a>解説  
 [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトには、 **Axes**コレクションが含まれています。 **セルセット**を開くと、このコレクションには少なくとも1つの**軸**が含まれます。 **軸**オブジェクトの使用方法の詳細については、 [axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md)オブジェクトに関する説明を参照してください。  
  
> [!NOTE]
>  **セルセット**のフィルター軸が**Axes**コレクションに含まれていません。 詳細については、 [Filteraxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) プロパティを参照してください。  
  
 **軸** は、標準の ADO コレクションです。 コレクションのプロパティとメソッドを使用して、次の操作を実行できます。  
  
-   [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、コレクション内のオブジェクトの数を取得します。  
  
-   既定の [Item](../../../ado/reference/ado-api/item-property-ado.md) プロパティを使用して、コレクションからオブジェクトを返します。  
  
-   [更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、プロバイダーからコレクション内のオブジェクトを更新します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [セルセットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axis オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
