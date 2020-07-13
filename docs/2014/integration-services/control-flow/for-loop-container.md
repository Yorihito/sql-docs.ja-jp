---
title: For ループ コンテナー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainerdetails.f1
helpviewer_keywords:
- repeating control flow
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ec872407dbec3885f72c4300b90cb3e11d1bcf92
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433039"
---
# <a name="for-loop-container"></a>For ループ コンテナー
  For ループ コンテナーは、パッケージ内で繰り返す制御フローを定義します。 ループの実装は、プログラミング言語の **For** ループ構造と同じです。 For ループ コンテナーは、ループの各繰り返しで式を評価し、式が `False` に評価されるまでそのワークフローを繰り返します。  
  
 For ループ コンテナーは、次の要素を使用してループを定義します。  
  
-   ループ カウンターに値を割り当てる、省略可能な初期化式。  
  
-   ループの停止または続行のテストに使用する式を含む、評価式。  
  
-   ループ カウンターを増減する、省略可能な初期化式。  
  
 次の図は、メール送信タスクの For ループ コンテナーを示しています。 初期化式が `@Counter = 0`の場合、評価式は `@Counter < 4`になり、初期化式が `@Counter = @Counter + 1`の場合、ループは 4 回繰り返して 4 つの電子メール メッセージを送信します。  
  
 ![タスクを 4 回繰り返す For ループ コンテナー](../media/ssis-forloop.gif "タスクを 4 回繰り返す For ループ コンテナー")  
  
 この式は、有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の式である必要があります。  
  
 初期化式および代入式を作成するには、代入演算子 (=) を使用します。 この演算子は、Integration Services の式文法以外ではサポートされておらず、For ループ コンテナーの初期化式および代入式の種類によってのみ、使用できます。 代入演算子を使用する式には、構文が必要です `@Var = <expression>` 。ここで、 **Var**は実行時の変数で、 \<expression> は式の構文の規則に従う式です [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 。 この式には、変数、リテラル、および、SSIS の式文法でサポートされるあらゆる演算子と関数を含めることができます。 この式は、変数のデータ型にキャスト可能なデータ型に評価される必要があります。  
  
 For ループ コンテナーでは、評価式を 1 つだけ含めることができます。 したがって、For ループ コンテナーは、すべての制御フローの要素を同一回数実行します。 For ループ コンテナーには、別の For ループ コンテナーを含めることができるため、パッケージ内で、入れ子になっているループを構築したり複合型のループを実装できます。  
  
 For ループ コンテナー上でトランザクションのプロパティを設定し、パッケージ制御フローのサブセットのトランザクションを定義できます。 この方法により、より細かなレベルでトランザクションを管理できます。 たとえば、For ループ コンテナーが、テーブル内のデータを複数回更新する制御フローを繰り返す場合、For ループおよびその制御フローを構成して、1 つでも正常に更新できないデータがある場合すべてのデータを更新しない、というトランザクションを使用できます。 詳細については、「 [Integration Services のトランザクション](../integration-services-transactions.md)」をご覧ください。  
  
## <a name="configuration-of-the-for-loop-container"></a>For ループ コンテナーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[For ループ エディター]](../for-loop-editor.md)  
  
-   [[式] ページ](../expressions/expressions-page.md)  
  
 プログラムによってこれらのプロパティを設定する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** クラスのドキュメントを参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
 Foreach ループ コンテナーの構成方法については、次のトピックを参照してください。  
  
-   [For ループ コンテナーを構成する](for-loop-container.md)  
  
-   [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>参照  
 [制御フロー](control-flow.md)   
 [Integration Services &#40;SSIS&#41; 式](../expressions/integration-services-ssis-expressions.md)  
  
  
