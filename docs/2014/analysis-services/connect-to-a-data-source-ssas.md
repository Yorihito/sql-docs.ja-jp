---
title: データソースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4fe7f7d5b31118369b8ce2a855b955e44f661dbc
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527228"
---
# <a name="connect-to-a-data-source-ssas"></a>[データ ソースへの接続] (SSAS)
  **テーブルのインポート ウィザード** のこのページを使用すると、リレーショナル データベース、データ フィード、ファイルなど、さまざまなデータ ソースに対する新しいデータ ソース接続を作成できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。 また、ワークスペースのデータベース サーバーにも適切なプロバイダーがインストールされている必要があります。 32 ビット (x86) サーバーの場合は、32 ビット プロバイダーがインストールされている必要があります。 64 ビット (x64) サーバーの場合は、64 ビット プロバイダーがインストールされている必要があります。  
  
 アーキテクチャに関係なく、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] は常に 32 ビット プロセスで実行されます。 64 ビット コンピューターで [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を実行している場合は、データ プロバイダーをインストールする際に、次の点に注意が必要です。  
  
-   32 ビットと 64 ビットのサイド バイ サイド インストールをサポートするプロバイダーの場合は、両方のプロバイダーをインストールする必要があります。  
  
-   ACE プロバイダーの場合は、64 ビット バージョンのプロバイダーをインストールする必要があります。 ACE プロバイダーは Office によって自動的にインストールされるため、ワークスペース データベース サーバーをホストする 64 ビット コンピューターでは 32 ビット バージョンの Microsoft Office を実行しないでください。  
  
     ACE プロバイダーは、テキスト ファイル、Excel ファイル、および Access ファイルからのインポートに使用されます。 これらのデータ ソースをサポートする必要がない場合は、64 ビットのワークスペース データベース サーバーが実行されているコンピューターで、32 ビット バージョンの Microsoft Office を実行してもかまいません。  
  
-   32 ビットと 64 ビットのサイド バイ サイド インストールをサポートしないその他のプロバイダーについては、32 ビットのプロバイダーをインストールする必要があります。 64 ビット コンピューターしか利用できない場合は、ワークスペース データベース サーバーとして 64 ビットのプロバイダーがインストールされたリモート コンピューターを使用してください。  
  
  
