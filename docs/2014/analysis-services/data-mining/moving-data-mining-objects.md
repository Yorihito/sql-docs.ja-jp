---
title: データマイニングオブジェクトの移動 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b10be3a79487376b173eab87059404b7f7a618e
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84521050"
---
# <a name="moving-data-mining-objects"></a>データ マイニング オブジェクトの移動
  データ マイニング オブジェクトを移動する最も一般的なシナリオは、テスト環境または分析環境から運用環境にモデルを配置する方法、または他のユーザーとモデルを共有する方法です。  
  
 このトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で用意されている、データ マイニング オブジェクトを移動するためのツールおよびスクリプト言語の使用方法について説明します。  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a>データベース間またはサーバー間でのデータ マイニング オブジェクトの移動  
 次の方法で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース間または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス間でデータ マイニング オブジェクトを移動できます。  
  
-   別のデータベースにソリューションを配置し直します。  
  
-   個々のオブジェクトのスクリプトを作成します。  
  
-   データベースをバックアップしてからそのコピーを復元します。  
  
-   構造とモデルをエクスポートおよびインポートします。  
  
 次のセクションでは、これらのオプションについて詳しく説明します。  
  
### <a name="deploying"></a>デプロイ中  
 ソリューションを別のサーバーまたはデータベースに配置するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用して作成されたソリューション ファイルが必要です。  
  
 Analysis Services ソリューションの配置の詳細については、「[Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)」を参照してください。  
  
### <a name="scripting"></a>スクリプト  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、オブジェクトのスクリプト作成に使用できる言語がいくつか用意されています。  
  
-   **XMLA:**[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクトを右クリックして、XMLA を使用してオブジェクトのスクリプトを作成することができます。 作成したスクリプトを実行するには、ターゲット サーバーの **XMLA クエリ** ウィンドウでスクリプトを開きます。  
  
-   **DMX:**[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で用意されているテンプレートまたはいずれかのクエリ ビルダーを使用して、スクリプトを作成できます。  
  
 ただし、スクリプト言語によって、実行できるタスクはそれぞれ異なります。  
  
-   オブジェクトの説明やデータ バインドなどのプロパティは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 言語を使用した場合のみ作成または変更できます。DMX を使用した場合は作成および変更できません。  
  
-   マイニング オブジェクトのインポートおよびエクスポートは、DMX でのみサポートされています。  
  
-   PMML の生成または PMML からのモデル定義のインポートは、DMX でのみサポートされています。  
  
-   アプリケーション データを使用したモデルのトレーニングは、DMX でのみサポートされています。 さらに、DMX INSERT INTO ステートメントでは、キー列の値を指定せずにモデルをトレーニングすることができます。  
  
 詳細については、「 [Analysis Services スクリプト言語 (ASSL) での開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。  
  
### <a name="backup-and-restore"></a>バックアップと復元  
 Analysis Services データベース全体のバックアップおよび復元は、データ マイニング ソリューションが OLAP オブジェクトに依存している場合に適しています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にはバックアップ/復元機能が用意されており、データベースをよりすばやく簡単にバックアップできます。  
  
 詳細については、「 [Analysis Services データベースのバックアップと復元](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」を参照してください。  
  
### <a name="exporting-and-importing"></a>エクスポートとインポート  
 DMX ステートメントを使用してマイニング モデルとマイニング構造をエクスポートし、インポートし直す方法は、リレーショナル データ マイニング オブジェクトを個別に移動したりバックアップしたりする場合に最も簡単です。 これらの操作の DMX 構文の詳細については、次のトピックを参照してください。  
  
-   [エクスポート &#40;DMX&#41;](/sql/dmx/export-dmx)  
  
-   [インポート &#40;DMX&#41;](/sql/dmx/import-dmx)  
  
 INCLUDE DEPENDENCIES オプションを指定すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって必要なデータ ソース ビューの定義もエクスポートされます。この場合、モデルや構造をインポートすると、ターゲット サーバーにデータ ソース ビューが再作成されます。 モデルのインポートが完了したら、オブジェクトに対して必要なマイニング権限を設定する必要があります。  
  
> [!NOTE]  
>  DMX を使用して OLAP モデルをエクスポートおよびインポートすることはできません。 マイニング モデルが OLAP キューブに基づいている場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で用意されている、データベース全体をバックアップおよび復元する機能を使用するか、キューブとモデルを配置し直す必要があります。  
  
## <a name="see-also"></a>参照  
 [データ マイニング ソリューションおよびオブジェクトの管理](management-of-data-mining-solutions-and-objects.md)  
  
  
