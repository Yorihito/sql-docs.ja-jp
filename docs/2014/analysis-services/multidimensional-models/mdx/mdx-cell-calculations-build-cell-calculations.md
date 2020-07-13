---
title: MDX でのセル計算の作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ab3219850c49c2ec16a12aab3ba7db67e9a8721
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546494"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a>MDX でのセル計算の作成 (MDX)
  多次元式 (MDX) では、計算されるメンバー、カスタム ロールアップ、およびカスタム メンバーなど、計算値を生成するための多数のツールを使用できます。 しかし、これらの機能を使用して特定のセル セットや、さらには単一セルに影響を与えるのは困難です。  
  
 セルに対して個別に計算値を生成するには、MDX の計算されるセル機能を使用する必要があります。 計算されるセルを使用すると、 *計算サブキューブ*と呼ばれる特定のセル スライスを定義し、計算サブキューブ内のすべてのセルに個別に式を適用できます。  
  
 計算されるセルでは、KPI で使用されるゴールシーク数式や推測分析の式などの複雑な機能を使用できます。 このレベルの機能は、パス順序の特定の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] パスに計算式を適用し、計算されるセルを使用して再帰的なパスを作成できるようにする、のパス順序機能から取得します。 パス順序の詳細については、「[パス順序と解決順序の概要 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)」を参照してください。  
  
 計算されるセルは、作成の有効範囲の点で、名前付きセットと計算されるメンバーの両方に似ています。計算されるセルは、セッションまたは 1 回のクエリの有効期限に合わせて一時的に作成することも、キューブの一部としてグローバルに使用可能にすることもできます。  
  
-   **クエリ スコープ** MDX クエリの一部として定義する、計算されるセルを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 その計算されるセルは、MDX の SELECT ステートメントの中で使用できます。 この方法では、`WITH` キーワードを使用して作成した計算されるセルを、SELECT ステートメントを修正せずに変更できます。  
  
     WITH キーワードを使用して計算されるメンバーを作成する方法の詳細については、「 [クエリ スコープのセル計算の作成 (MDX)](../../multidimensional-models-olap-logical-cube-objects/calculations.md)」を参照してください。  
  
-   **セッション スコープ** クエリのコンテキストよりも広いスコープを設定して計算されるセルを作成する場合 (つまり、スコープを MDX セッションの有効期間全体とする場合) は、CREATE CELL CALCULATION または ALTER CUBE ステートメントのいずれかを使用します。  
  
     CREATE CELL CALCULATION または ALTER CUBE ステートメントを使用してセッションでの計算されるセルを作成する方法の詳細については、「 [セッション スコープの計算されるセルの作成](mdx-cell-calculations-session-scoped-calculated-cells.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ALTER CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube)   
 [CREATE CELL CALCULATION ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation)   
 [MDX&#41;&#40;クエリスコープのセル計算を作成する](../../multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
