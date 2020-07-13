---
title: ドライバーのバージョンスキーム |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 864a8bd892315b060fc6fcf42dbe69dfea61ae59
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303453"
---
# <a name="driver-version-scheme"></a>ドライバー バージョン スキーム
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 次の表に、Microsoft ODBC Driver for Oracle のすべてのリリースバージョンを示します。  
  
|ドライバーのバージョン|ビルド番号|可用性の履歴|  
|--------------------|------------------|--------------------------|  
|1.0|2.00.6235|Visual C++ 4.2 および Visual Basic 5.0 Enterprise Edition|  
|2.0|2.73.7269|Visual Studio 97 および MDAC 1.5 a|  
|2.0 更新|2.73.7283.01|IIS 4.0|  
|2.0 更新|2.73.7283.03|MDAC 1.5 b および 1.5 c|  
|2.0 更新|2.73.7356|ODBC 3.5 SDK|  
|2.5|2.573.2927|Visual Studio 6.0 および MDAC 2.0|  
|2.5 更新|2.573.3513|SQL Server 7.0<br /><br /> SQL Server 6.5 SP5|  
  
 Build 2.00.6235 (バージョン 1) は、Microsoft ODBC Driver for Oracle の最初のリリースでした。 最初のバージョンのリリース後、新しい名前付け規則が採用されました。  
  
 たとえば、2.73.7283.03 は次の個別のコンポーネントに分けることができます。  
  
-   2 = バージョン番号。  
  
-   73 = ドライバーが設計されている Oracle サーバーのバージョン。  
  
-   7283.03 = ドライバーのビルド番号。  
  
> [!NOTE]  
>  Release 2.573.2973 では、名前付け規則によって、2.573 が2.73 よりも前のリリースであるという混乱が生じましたが、ビルド番号の各セクションは個別に考慮する必要があります。 数値573は73よりも大きいため、新しいバージョンです。 また、"2.5" はドライバーのバージョン番号を示します。
