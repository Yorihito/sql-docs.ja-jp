---
title: 'レッスン 9: パースペクティブの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20601a1ece7707e8f798907f21ee5ee7110fe2fe
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542224"
---
# <a name="lesson-9-create-perspectives"></a>レッスン 9: パースペクティブを作成する
  このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブでは、表示可能なモデルのサブセットを定義して、集中的、ビジネス固有またはアプリケーション固有のビューポイントを作成できます。 パースペクティブを使用してモデルに接続すると、そのパースペクティブ内に定義されたモデル オブジェクト (テーブル、列、メジャー、階層、および KPI) のみがフィールドとして表示されます。  
  
 このレッスンで作成する Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。 特定のオブジェクトをビューから除外するパースペクティブを作成した場合、そのオブジェクトはモデル内に依然として存在しますが、レポート クライアントのフィールドの一覧には表示されなくなります。 計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。  
  
 このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。 後でこのモデルにテーブルを追加する場合は、追加のパースペクティブを作成して、モデルに対する異なるビューポイント (Inventory や Sales Force など) を定義できます。  
  
 詳細については、「[パースペクティブ (SSAS テーブル)](tabular-models/perspectives-ssas-tabular.md)」を参照してください。  
  
 このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「 [レッスン 8: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)」を完了している必要があります。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  モデルデザイナーで、[**モデル**] メニューをクリックし、[**パースペクティブ**] をクリックします。  
  
2.  **[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]** をクリックします。  
  
3.  パースペクティブの名前を変更するには、[**新しいパースペクティブ 1** ] 列見出しをダブルクリックし、「」と入力し `Internet Sales` ます。  
  
4.  [**フィールド**] で、 **Date**、 **Geography**、 **Product**、 **product Category**、 **product サブカテゴリ**、およびの各テーブルを選択し `Internet Sales` ます。  
  
     Customer テーブルおよびそのすべての列をこのパースペクティブから除外したことに注意してください。 後ほど、レッスン 12 で、"Excel で分析" 機能を使用してこのパースペクティブをテストします。 Excel ピボットテーブルのフィールドの一覧には、Customer テーブルを除く各テーブルが含まれます。  
  
5.  選択内容を確認し、 **Customer** テーブルがオフになっていることを確認して、 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 10: 階層の作成](lesson-9-create-hierarchies.md)」に進んでください。  
  
  
