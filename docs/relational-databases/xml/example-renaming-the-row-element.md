---
title: '例 : &lt;row&gt; 要素の名前を変更する | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c9a082f5bd5159f8b1dc32c3c9e2ba233cce817b
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664521"
---
# <a name="example-renaming-the-ltrowgt-element"></a>例 : &lt;row&gt; 要素の名前を変更する
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  結果セットの各行では、RAW モードによって `<row>`要素が生成されます。 次のクエリに示すように、必要に応じて、RAW モードへの省略可能な引数を指定することにより、この要素に別の名前を指定できます。 クエリでは、行セットの行ごとに <`ProductModel`> 要素が返されます。  
  
## <a name="example"></a>例  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 結果は次のとおりです。 `ELEMENTS` ディレクティブがクエリに追加されたので、結果は要素中心になります。  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
