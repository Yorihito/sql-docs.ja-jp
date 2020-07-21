---
title: このブックには外部データを更新する 1 つ以上のクエリが含まれています。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e13b648b35cb0a6b6d9272ec9a2b9d560c3c7f4
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547744"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>このブックには外部データを更新する 1 つ以上のクエリが含まれています。
  PowerPivot データが含まれる Excel ブックの場合、Excel Services は接続情報が検出されるとこの警告を表示し、このブックのクエリを有効にするか無効にするかを確認するプロンプトを表示します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|PowerPivot for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Excel Services がデータ更新時に警告を表示するように構成されています。|  
|メッセージ テキスト|このブックには外部データを更新する 1 つ以上のクエリが含まれています。 悪意のあるユーザーは資格情報にアクセスし、他のユーザーに配布したり、他の有害なアクションを実行するようにクエリを書き換えることがあります。<br /><br /> このブックのソースを信頼できる場合は、[はい] をクリックしてこのブックの外部データに対するクエリを有効にします。 信頼できるかどうかが不明である場合は、[いいえ] をクリックして変更がブックに適用されないようにします。<br /><br /> このブックの外部データへのクエリを有効にしますか?|  
  
## <a name="explanation"></a>説明  
 PowerPivot ブックに、データの読み込みと計算を行う外部 PowerPivot サーバーと通信する Excel で使用される埋め込みデータ接続文字列が含まれています。 [データ更新に関する警告を表示する] が有効になっている場合、Excel Services はこの接続文字列を検出し、ユーザーにその旨を警告します。  
  
 ブックの PowerPivot データをフィルターおよびスライスする場合は、クエリを有効にする必要があります。 信頼できる PowerPivot ブックのクエリのみを有効にしてください。  
  
## <a name="user-action"></a>ユーザーの操作  
 **[はい]** をクリックしてクエリを有効にします。  
  
 また、構成設定を変更して、更新時に警告が表示されないようにすることもできます。  
  
1.  サーバーの全体管理で、[アプリケーション管理] の [**サービスアプリケーションの管理**] をクリックします。  
  
2.  **[Excel Services アプリケーション]** をクリックします。  
  
3.  **[信頼できるファイル保存場所]** をクリックします。  
  
4.  **[http://]** または構成する場所をクリックします。  
  
5.  [外部データ] で、 **[データ更新に関する警告を表示する]** チェック ボックスをオフにします。  
  
6.  **[OK]** をクリックします。  
  
 または、PowerPivot ブックが含まれるサイト用に新しく信頼できる場所を作成し、そのサイトの構成設定だけを変更することもできます。 詳細については、「 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
  
