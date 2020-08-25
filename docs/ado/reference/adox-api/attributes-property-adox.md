---
description: Attributes プロパティ (ADOX)
title: Attributes プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::put_Attributes
- _Column::Attributes
- _Column::PutAttributes
- _Column::get_Attributes
- _Column::GetAttributes
helpviewer_keywords:
- Attributes property [ADOX]
ms.assetid: e3abb359-79a3-4c22-b3a8-2900817e0d23
author: rothja
ms.author: jroth
ms.openlocfilehash: b2fca7e2cf9bce25d1993d16d4ec6a44bf53ef67
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771351"
---
# <a name="attributes-property-adox"></a>Attributes プロパティ (ADOX)
列の特性について説明します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **Long 型**の値を設定または返します。 値は、 [Column](./column-object-adox.md) オブジェクトによって表されるテーブルの特性を指定します。 この値には、 [Columnsystem.enum 列挙](./columnattributesenum.md) 定数の組み合わせを指定できます。 既定値はゼロ (**0**) です。これは、 **Adcolfixed** でも **adcolfixed**でもありません。  
  
## <a name="applies-to"></a>適用対象  
  
- [Column オブジェクト (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [Attributes プロパティの例 (VB)](./attributes-property-example-vb.md)