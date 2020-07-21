---
title: ローカルキューブ (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75f02dd54992e9cc4f94d9845e0e25de5ed988f2
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545944"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a>ローカル キューブ (Analysis Services - 多次元データ)
  ローカル キューブを作成、更新、または削除するには、ASSL スクリプトまたは AMO プログラムを作成して実行する必要があります。  
  
 ローカル キューブおよびローカル マイニング モデルは、クライアント ワークステーションがネットワークから切断されている間も分析が可能です。 たとえば、次の図のように、クライアント アプリケーションが OLE DB for OLAP 9.0 Provider (MSOLAP.3) を呼び出すと、このプロバイダーはローカル キューブ エンジンを読み込み、ローカル キューブを作成してクエリを実行します。  
  
 ![ローカル キューブとローカル モデルのクライアント アーキテクチャ](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "ローカル キューブとローカル モデルのクライアント アーキテクチャ")  
  
 ADMOD.NET および分析管理オブジェクト (AMO) もまた、ローカル キューブとやり取りするときにローカル キューブ エンジンを読み込みます。 ローカル キューブ エンジンはローカル キューブと接続するときにローカル キューブ ファイルを排他的にロックするため、ローカル キューブ ファイルには同時に 1 つのプロセスしかアクセスできません。 1 つのプロセスにつき、5 つまでの同時接続が可能です。  
  
 .cub ファイルには、2 つ以上のキューブまたはデータ マイニング モデルが含まれる場合があります。 ローカル キューブおよびデータ マイニング モデルに対するクエリは、ローカル キューブ エンジンによって処理されるので、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスへの接続は必要ありません。  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] をローカル キューブの管理に使用することはできません。  
  
## <a name="local-cubes"></a>ローカル キューブ  
 ローカルキューブを作成し、インスタンス内の既存のキューブ、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] またはリレーショナルデータソースから設定することができます。  
  
|ローカル キューブ用データのソース|作成方法|  
|------------------------------------|---------------------|  
|サーバーベースのキューブ|CREATE GLOBAL CUBE ステートメントまたは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) スクリプトを使用して、サーバーベースのキューブからキューブを作成および設定できます。 詳細については、「 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) 」または「 [Analysis Services スクリプト言語 &#40;Assl&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。|  
|リレーショナルデータソース|ASSL スクリプトを使用して、OLE DB リレーショナル データベースからキューブを作成して設定します。 ASSL を使用してローカル キューブを作成するには、ローカル キューブ ファイル (*.cub) に接続して、サーバー キューブを作成するときに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスで ASSL スクリプトを実行するのと同じ要領で ASSL スクリプトを実行するだけです。 詳細については、「 [Analysis Services Scripting Language &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。|  
  
 ローカル キューブを再構築してデータを更新するには、REFRESH CUBE ステートメントを使用します。 詳細については、「 [REFRESH CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube)」を参照してください。  
  
### <a name="local-cubes-created-from-server-based-cubes"></a>サーバーベースのキューブから作成されたローカル キューブ  
 サーバーベースのキューブからローカル キューブを作成する場合は、次の点に注意してください。  
  
-   個別のカウント メジャーはサポートされていません。  
  
-   メジャーを追加する場合は、追加するメジャーに関連するディメンションも最低 1 つ追加する必要があります。 メジャーグループに対するディメンションリレーションシップの詳細については、「[ディメンションリレーションシップ](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。  
  
-   親子階層を追加すると、親子階層のレベルやフィルターは無視されて、親子階層全体が追加されます。  
  
-   メンバー プロパティは作成されません。  
  
-   準加法メジャーを含める場合、Account ディメンションおよび Time ディメンションでのスライスは許可されていません。  
  
-   参照ディメンションは常に具体化されます。  
  
-   多対多ディメンションを含めると、次のルールが適用されます。  
  
    -   多対多ディメンションをスライスすることはできません。  
  
    -   中間メジャー グループのメジャーを追加する必要があります。  
  
    -   多対多リレーションシップに関係する 2 つのメジャー グループに共通するディメンションはスライスすることができません。  
  
-   ローカル キューブに追加されたメジャーおよびディメンションに依存する計算されるメンバー、名前付きセット、および割り当てだけがローカル キューブに表示されます。 無効な計算されるメンバー、名前付きセット、および割り当ては自動的に除外されます。  
  
### <a name="security"></a>セキュリティ  
 ユーザーがサーバーキューブからローカルキューブを作成できるようにするには、サーバーキューブに対する**ドリルスルー権限とローカルキューブ**権限がユーザーに与えられている必要があります。 詳細については、「 [Grant cube or model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)」を参照してください。  
  
 ローカル キューブは、サーバー キューブのようにロールを使用してセキュリティで保護されていません。 ローカル キューブ ファイルへのファイル レベルのアクセス権を持っていれば、ローカル キューブ ファイル内のキューブに対してクエリを実行できます。 ローカル キューブ ファイルに対して `Encryption Password` 接続プロパティを使用すると、ローカル キューブ ファイルにパスワードを設定できます。 ローカル キューブ ファイルにパスワードを設定すると、以後クエリを実行するためにローカル キューブ ファイルに接続するときにそのパスワードが必要になります。  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#40;のグローバルキューブステートメントの作成](/sql/mdx/mdx-data-definition-create-global-cube)   
 [Analysis Services スクリプト言語 &#40;ASSL&#41;を使用した開発](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [MDX&#41;&#40;CUBE ステートメントの更新](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
