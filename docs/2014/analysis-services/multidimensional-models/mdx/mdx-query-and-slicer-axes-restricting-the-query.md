---
title: クエリ軸とスライサー軸を使用したクエリの制限 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed4d50aa40d2915c60f887e64cdc3ef8a6d52c5c
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546274"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>クエリ軸とスライサー軸によるクエリの制限 (MDX)
  多次元式 (MDX) の SELECT ステートメントを作成する場合、アプリケーションでは通常、キューブを調べ、階層のセットを以下の 2 つのサブセットに分けます。  
  
-   **クエリ軸**-複数のメンバーについてデータを取得する階層のセット。 クエリ軸の詳細については、「[クエリ軸の内容の指定 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。  
  
-   **スライサー軸**-1 つのメンバーについてデータを取得する階層のセット。 スライサー軸の詳細については、「[スライサー軸の内容の指定 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)」を参照してください。  
  
 クエリ軸とスライサー軸は、クエリの実行対象であるキューブの複数の階層で構成できるため、これらの用語によって、クエリの実行対象であるキューブで使用される階層と、MDX クエリで返されたキューブで作成される階層とを区別しています。  
  
 クエリ軸のスライサー軸を使用する単純な例については、「[Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)」(クエリ軸とスライサー軸を使用する簡単な例) を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
