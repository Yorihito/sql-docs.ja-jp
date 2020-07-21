---
title: コードの自動作成 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9183495887233e94d9ff43a52e04eaf5ed3c6b36
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972182"
---
# <a name="automatic-code-creation-master-data-services"></a>コードの自動作成 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、Code 属性の数値または他の数値属性の数値を自動的に生成できます。 コードを自動生成するときは、コードに他の値を入力してもかまいません。正確には、初期値が自動的に設定されます。  
  
## <a name="generating-code-values"></a>コード値の生成  
 管理者は、関連付けられているエンティティのプロパティを編集することによって、Code 属性の値の自動生成を構成できます。 初期値を指定でき、後続の各値は 1 ずつ増分されます。  
  
 いずれかのツールで、またはステージング処理を使用してコード値を MDS に入力するとき、コード値をブランクのままにすると、コード値が自動的に生成されます。 または、自分で選択したコード値を指定することもできます。  
  
## <a name="generating-other-attribute-values"></a>他の属性値の生成  
 管理者は、ビジネス ルールを作成することによって、Code 以外の属性値を自動的に生成できます。 初期値を指定できるだけでなく、後続の各値での増分値も指定できます。  
  
 いずれかのツールで、またはステージング処理を使用して属性値を MDS に入力するとき、属性値をブランクのままにできます。 ビジネス ルールが適用されると、既存の最高の値に基づいて値が増分されます。 たとえば、ルールが "1 から開始して 4 ずつ増加する生成値に対する既定の属性" であり、属性の現在最も高い値が 700 である場合、追加される次のメンバーの値は 704 になります。  
  
## <a name="deleting-automatically-generated-values"></a>自動的に生成される値の削除  
 管理者が Code 属性の値の自動生成を有効にした後、ユーザーが再利用するコード値を持っていたメンバーを誤って削除する場合があります。 "メンバーコードは既に削除されたメンバーによって使用されています" というエラーメッセージが表示されます。 この解決方法には、次の 2 つが挙げられます。  
  
-   管理者は、[**バージョン管理**] 機能領域で、メンバーが削除されたときに発生したトランザクションを元に戻すことができます。 ただし、これは、以前のメンバーの属性と階層とコレクションのメンバーシップがすべて復元されることを意味します。 詳細については、「[トランザクションの反転 &#40;マスターデータサービス&#41;](reverse-a-transaction-master-data-services.md)」を参照してください。  
  
-   管理者は、ステージング処理を使用して、メンバーを完全に削除できます。 詳細については、「 [&#40;マスターデータサービス&#41;のステージング処理を使用したメンバーの非アクティブ化または削除](add-update-and-delete-data-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|Code 属性の値を自動的に生成します。|[Code 属性の値の自動生成 (マスター データ サービス)](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|他の属性の値を自動的に生成します。|[Code 以外の属性の値の自動生成 (マスター データ サービス)](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [マスター データ サービス概要](master-data-services-overview-mds.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [エンティティ (マスター データ サービス)](../../2014/master-data-services/entities-master-data-services.md)  
  
  
