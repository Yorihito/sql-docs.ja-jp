---
title: ファクトリレーションシップとファクトリレーションシップのプロパティを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15f67a4bdf699bbc6443fc76ce54bcfb35831827
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547094"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>ファクト リレーションシップとファクト リレーションシップのプロパティの定義
  新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ファクト ディメンションのリレーションシップが存在するかどうかを検出し、ディメンションの使用法を `Fact` に設定しようと試みます。 ファクト ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。 ディメンションとメジャー グループ間のファクト リレーションシップには次の制約があります。  
  
-   1 つのキューブ ディメンションには、特定のメジャー グループに対してファクト リレーションシップを 1 つだけ設定できます。  
  
-   1 つのキューブ ディメンションには、複数のメジャー グループに対して個別のファクト リレーションシップを設定できます。  
  
-   リレーションシップの粒度属性は、ディメンションのキー属性 (取引番号など) である必要があります。 これにより、ディメンションとファクト テーブル内のファクトとの間に一対一リレーションシップが作成されます。  
  
  
