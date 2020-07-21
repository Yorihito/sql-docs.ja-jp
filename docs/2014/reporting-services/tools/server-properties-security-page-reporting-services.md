---
title: '[サーバーのプロパティ] ([セキュリティ] ページ) - Reporting Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a49f56c4e898b0189ce0f8bf5008873e13dc6223
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099556"
---
# <a name="server-properties-security-page---reporting-services"></a>[サーバーのプロパティ]\([セキュリティ] ページ) - Reporting Services
  このページを使用すると、レポート サーバーを危険にさらす可能性のある機能を無効にできます。 これらの機能を無効にすることで一部の機能が制限されますが、特定の脅威を緩和することで、レポート サーバー全体のセキュリティを向上させることができます。  
  
 このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]** をクリックします。 **[セキュリティ]** をクリックすると、このページが開きます。  
  
## <a name="options"></a>オプション  
 **[レポート データ ソースで Windows 統合セキュリティを有効にする]**  
 レポートを要求したユーザーの Windows セキュリティ トークンを使用してレポート データ ソースに接続するかどうかを指定します。  
  
 この機能を無効にすると、レポート データ ソースのプロパティ ページにある Windows 統合セキュリティ機能は使用できなくなります。 レポート データ ソースが Windows 統合セキュリティを使用するように構成されている場合、この機能を無効にすると、レポート サーバーによってすべてのデータ ソース接続プロパティが即時に更新され、資格情報が要求されるようになります。  
  
 **[カスタム レポートを有効にする]**  
 ユーザーがレポート ビルダーのレポートからアドホック クエリを実行できるようにするかどうかを指定します。実行できるようにした場合は、ユーザーが対象データをクリックすると新しいレポートが自動的に生成されます。  
  
 このオプションの設定によって、レポート サーバー上の `EnableLoadReportDefinition` プロパティの設定が `True` になるか `False` になるかが決まります。 このオプションをオフにするとプロパティが `False` に設定され、レポート サーバーはデータ探索中に作成されるクリックスルー レポートを生成しません。 `LoadReportDefinition` メソッドの呼び出しはすべてブロックされます。  
  
 この機能を無効にすることで、悪意のあるユーザーによる `LoadReportDefinition` 要求でレポート サーバーが過負荷になるサービス拒否攻撃の脅威を軽減することができます。  
  
## <a name="see-also"></a>参照  
 [レポートサーバーのプロパティ &#40;Management Studio の設定&#41;](set-report-server-properties-management-studio.md)   
 [Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [レポートデータソースの資格情報と接続情報を指定してください](..[Management Studio の F1 ヘルプでレポートサーバーを](report-server-in-management-studio-f1-help.md)作成します (& o)。これには、レポートサーバーを使用します。  
  
  
