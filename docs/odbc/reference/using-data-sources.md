---
title: データソースの使用 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df9b09e4c5519e0fff44902bd83b8e3d92a67ca8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286553"
---
# <a name="using-data-sources"></a>データ ソースの使用
通常、データソースは、エンドユーザーまたは*ODBC 管理者*と呼ばれるプログラムがある技術者によって作成されます。 ODBC 管理者は、ドライバーが使用することをユーザーに確認してから、そのドライバーを呼び出すことができます。 ドライバーによって、データソースに接続するために必要な情報を要求するダイアログボックスが表示されます。 ユーザーが情報を入力すると、ドライバーはシステムに情報を格納します。  
  
 その後、アプリケーションはドライバーマネージャーを呼び出し、コンピューターのデータソースの名前またはファイルのデータソースを含むファイルのパスを渡します。 コンピューターのデータソース名を渡すと、ドライバーマネージャーはシステムを検索して、データソースによって使用されているドライバーを検索します。 次に、ドライバーを読み込んで、データソース名を渡します。 ドライバーは、データソース名を使用して、データソースに接続するために必要な情報を検索します。 最後に、データソースに接続します。通常は、ユーザーにユーザー ID とパスワードの入力を求めます。この場合、通常は保存されません。  
  
 ファイルデータソースが渡されると、ドライバーマネージャーがファイルを開き、指定されたドライバーを読み込みます。 ファイルに接続文字列も含まれている場合は、これをドライバーに渡します。 接続文字列の情報を使用して、ドライバーはデータソースに接続します。 接続文字列が渡されなかった場合、通常、ドライバーはユーザーに必要な情報の入力を求めます。
