---
title: 変数とパラメーターの使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd01cf78ea5e3284aa51cad7dc848176a5dc9298
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546164"
---
# <a name="using-variables-and-parameters-mdx"></a>変数とパラメーターの使用 (MDX)
  では [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、多次元式 (MDX) ステートメントをパラメーター化できます。 ステートメントをパラメーター化すれば、実行時にカスタマイズ可能な汎用ステートメントを作成できます。  
  
 パラメーター化されたステートメントを作成するときには、パラメーター名の前に @ 記号を付けることによってパラメーター名を識別します。 たとえば、は @Year 有効なパラメーター名です。  
  
 MDX は、リテラルまたはスカラー値用のパラメーターだけをサポートします。 メンバー、セット、または組を参照するパラメーターを作成するには、 [StrToMember](/sql/mdx/strtomember-mdx) や [StrToSet](/sql/mdx/strtoset-mdx)などの関数を使う必要があります。  
  
 次の XML for Analysis (XMLA) の例では、 @CountryName 顧客データを取得する国がパラメーターに含まれています。  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 OLE DB でこの機能を使用するには、`ICommandWithParameters` インターフェイスを使用します。 ADOMD.Net でこの機能を使用するには、 **AdomdCommand.Parameters** コレクションを使用します。  
  
## <a name="see-also"></a>参照  
 [MDX スクリプティングの基礎 &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  
