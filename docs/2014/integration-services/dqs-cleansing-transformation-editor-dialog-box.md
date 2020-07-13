---
title: '[DQS クレンジング変換エディター] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3f16adec193cebde1d30d1455e68240622b4ded8
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437429"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a>[DQS クレンジング変換エディター] ダイアログ ボックス
  **[DQS クレンジング変換エディター]** ダイアログ ボックスを使用すると、Data Quality Services (DQS) を使用してデータを修正できます。 詳細については、「 [Data Quality Services の概念](../../2014/data-quality-services/data-quality-services-concepts.md)」を参照してください。  
  
 変換の詳細については、「 [DQS クレンジング変換](data-flow/transformations/dqs-cleansing-transformation.md)」を参照してください。  
  
 **どうしたいんですか。**  
  
-   [DQS クレンジング変換エディターを開く](#open)  
  
-   [[接続マネージャー] タブのオプションの設定](#connection)  
  
-   [[マッピング] タブのオプションの設定](#mapping)  
  
-   [[詳細設定] タブのオプションの設定](#advanced)  
  
-   [[DQS クレンジング接続マネージャー] ダイアログ ボックスのオプションの設定](#manager)  
  
##  <a name="open-the-dqs-cleansing-transformation-editor"></a><a name="open"></a>DQS クレンジング変換エディターを開く  
  
1.  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、DQS クレンジング変換を [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに追加します。  
  
2.  コンポーネントを右クリックし、 **[編集]** をクリックします。  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> [接続マネージャー] タブのオプションの設定  
 **[データ品質接続マネージャー]**  
 既存の DQS 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[DQS クレンジング接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。 「 [[DQS クレンジング接続マネージャー] ダイアログ ボックスのオプションの設定](#manager)」を参照してください。  
  
 **[データ品質ナレッジ ベース]**  
 接続されたデータ ソースの既存の DQS ナレッジ ベースを選択します。 DQS サポート技術情報の詳細については、「 [DQS のナレッジ ベースとドメイン](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。  
  
 **暗号化接続**  
 DQS サーバーとの間のデータ転送を暗号化するために、接続を暗号化するかどうかを指定し [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。  
  
 **[使用できるドメイン]**  
 選択されたナレッジ ベースで使用できるドメインを一覧表示します。 ドメインには、単一ドメインと、2 つ以上の単一ドメインが含まれた複合ドメインの 2 種類があります。  
  
 複合ドメインに列をマップする方法については、「 [複合ドメインへの列のマップ](data-flow/transformations/map-columns-to-composite-domains.md)」を参照してください。  
  
 ドメインの詳細については、「 [DQS のナレッジ ベースとドメイン](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。  
  
 **[エラー出力の構成]**  
 行レベルのエラーを処理する方法を指定します。 接続されたデータ ソースのデータを変換で修正する際には、予期しないデータ値や検証制約が原因でエラーが発生することがあります。  
  
 有効な値は次のとおりです。  
  
-   **[エラー コンポーネント]**: 変換に失敗したこと、およびデータが Data Quality Services データベースに挿入されていないことを示します。 これが既定値です。  
  
-   **[行のリダイレクト]**: 入力データが Data Quality Services データベースに挿入されていないために、エラー出力にリダイレクトされることを示します。  
  
##  <a name="set-options-on-the-mapping-tab"></a><a name="mapping"></a>[マッピング] タブのオプションの設定  
 複合ドメインに列をマップする方法については、「 [複合ドメインへの列のマップ](data-flow/transformations/map-columns-to-composite-domains.md)」を参照してください。  
  
 **[使用できる入力列]**  
 接続されたデータ ソースの列を一覧表示します。 修正するデータを含む 1 つまたは複数の列を選択します。  
  
 **入力列**  
 **[使用できる入力列]** 領域で選択した入力列を一覧表示します。  
  
 **ドメイン**  
 入力列にマップするドメインを選択します。  
  
 **[ソースの別名]**  
 元の列値を含むソース列を一覧表示します。  
  
 列名を変更するフィールドをクリックしてください。  
  
 **出力のエイリアス**  
 **DQS クレンジング変換**によって出力された列を一覧表示します。 この列には、元の列値または修正後の値が含まれます。  
  
 列名を変更するフィールドをクリックしてください。  
  
 **[状態の別名]**  
 修正されたデータの状態情報を含む列を一覧表示します。 列名を変更するフィールドをクリックしてください。  
  
##  <a name="set-options-on-the-advanced-tab"></a><a name="advanced"></a>[詳細設定] タブのオプションの設定  
 **[出力の標準化]**  
 ドメインで定義されている出力形式に基づいて標準化された形式でデータを出力するかどうかを示します。 標準化された形式の詳細については、「 [データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」を参照してください。  
  
 **Confidence**  
 修正されたデータの信頼レベルを含めるかどうかを示します。 信頼レベルは、DQS の修正または候補に対する確実性の度合いを示します。 信頼レベルの詳細については、「 [データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」を参照してください。  
  
 **理由**  
 データ修正の理由を含めるかどうかを示します。  
  
 **[追加されたデータ]**  
 既存の参照データ プロバイダーから取得した追加データを出力するかどうかを示します。 詳細については、「 [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)」をご覧ください。  
  
 **[追加されたデータ スキーマ]**  
 データ スキーマを出力するかどうかを示します。 詳細については、「[参照データへのドメインまたは複合ドメインのアタッチ](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)」を参照してください。  
  
##  <a name="set-the-options-in-the-dqs-cleansing-connection-manager-dialog-box"></a><a name="manager"></a>[DQS クレンジング接続マネージャー] ダイアログボックスのオプションの設定  
 **サーバー名**  
 接続先の DQS サーバーの名前を選択または入力します。 サーバーの詳細については、「 [DQS 管理](../../2014/data-quality-services/dqs-administration.md)」を参照してください。  
  
 **接続をテスト**  
 クリックすると、指定した接続が利用可能であることを確認できます。  
  
 次の方法で、接続領域から **[DQS クレンジング接続マネージャー]** ダイアログ ボックスを開くこともできます。  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、既存の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開くか、新しいプロジェクトを作成します。  
  
2.  接続領域内を右クリックし、 **[新しい接続]** をクリックして、 **[DQS]** をクリックします。  
  
3.  **[追加]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [データ ソースにデータ品質ルールを適用する](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  
