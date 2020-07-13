---
title: モデリングフラグの表示または変更 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3ad72ec94c8125b2f3bd9067a3a2ce413eeaba21
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520198"
---
# <a name="view-or-change-modeling-flags-data-mining"></a>モデリング フラグの表示または変更 (データ マイニング)
  モデリング フラグは、マイニング構造列またはマイニング モデル列に設定して、分析時にアルゴリズムがデータを処理する方法を制御するためのプロパティです。  
  
 データ マイニング デザイナーでは、マイニング構造やマイニング列に関連付けられているモデリング フラグを、その構造またはモデルのプロパティを表示することによって表示および変更することができます。 DMX、AMO、または XMLA を使用してモデリング フラグを設定することもできます。  
  
 この手順では、デザイナーでモデリング フラグを変更する方法について説明します。  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>構造列またはモデル列のモデリング フラグの表示または変更  
  
1.  SQL Server Design Studio で、ソリューション エクスプローラーを開き、マイニング構造をダブルクリックします。  
  
2.  NOT NULL モデリングフラグを設定するには、[**マイニング構造**] タブをクリックします。リグレッサーフラグまたは MODEL_EXISTENCE_ONLY フラグを設定するには、[**マイニングモデル**] タブをクリックします。  
  
3.  表示または変更する列を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  新しいモデリング フラグを追加するには、 **[ModelingFlags]** プロパティの横にあるテキスト ボックスをクリックし、使用するモデリング フラグのチェック ボックスをオンにします。  
  
     その列のデータ型に合ったモデリング フラグのみが表示されます。  
  
    > [!NOTE]  
    >  モデリング フラグを変更した後、モデルを再処理する必要があります。  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>モデルで使用されているモデリング フラグの取得  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、DMX クエリ ウィンドウを開き、次のようなクエリを入力します。  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>参照  
 [マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md)   
 [モデリング フラグ (データ マイニング)](modeling-flags-data-mining.md)  
  
  
