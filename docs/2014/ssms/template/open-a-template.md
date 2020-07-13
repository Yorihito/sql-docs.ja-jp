---
title: テンプレートを開く | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ad12b20233cb753b28c4618ce53cd28ed850984c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061946"
---
# <a name="open-a-template"></a>テンプレートを開く
  テンプレート エクスプローラーからテンプレートを開くことができます。  
  
## <a name="to-open-a-template-from-template-explorer"></a>テンプレート エクスプローラーからテンプレートを開くには  
 テンプレート エクスプローラーからテンプレートを開くことができます。  
  
1.  テンプレート エクスプローラーを開くには、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  テンプレート カテゴリの一覧で、開こうとしているテンプレートを含むカテゴリを展開します。  
  
3.  テンプレートを開くには、次の 3 とおりの方法があります。  
  
    1.  テンプレートをダブルクリックしてコード エディター ウィンドウで開きます。  
  
    2.  テンプレートを右クリックして **[開く]** を選択し、コード エディター ウィンドウで開きます。  
  
    3.  テンプレートをコード エディター ウィンドウにドラッグし、テンプレート コードをエディター ウィンドウの内容に追加します。  
  
 テンプレートを開いた後、 **[テンプレート パラメーターの値の指定]** ダイアログ ボックスでテンプレート パラメーターを適切な値に置き換えます。  
  
 テンプレートを開いて新しいエディター ウィンドウが起動する場合、そのウィンドウは、現在のアクティブな接続の資格情報によって開きます。 たとえば、CREATE DATABASE テンプレートを開くときに、オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスにフォーカスがあると、そのインスタンスへの接続を使用して新しいエディター ウィンドウが開きます。 アクティブな接続がない場合は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によってログイン ダイアログが表示されます。  
  
## <a name="see-also"></a>参照  
 [テンプレートエクスプローラー](template-explorer.md)   
 [テンプレート パラメーターの置換](replace-template-parameters.md)  
  
  
