---
title: '[ポリシーのインポート] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5820a49a51358a409e5f87ddca0b79c797a9eeab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063873"
---
# <a name="import-policies-dialog-box"></a>[ポリシーのインポート] ダイアログ ボックス
  このダイアログ ボックスを使用すると、XML ファイルとして保存された 1 つ以上のポリシー (およびその参照された条件) を [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の現在のインスタンスにインポートできます。  
  
## <a name="options"></a>オプション  
 **[インポートするファイル]**  
 XML ファイルからポリシーをインポートするには、ファイルのパスと名前を入力するか、参照ボタン ( **[...]** ) を使用します。  
  
 **[インポートされるアイテムと重複部分を置き換える]**  
 この [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに同じ名前のポリシーまたは条件が既に存在する場合、その既存のポリシーまたは条件が上書きされます。 依存ポリシーを使用している条件は、依存ポリシーも上書きしない限り上書きできません。 このオプションを選択していない場合は、同じ条件式を使用している既存の条件によってエラーが発生することはありません。  
  
 **[ポリシーの状態]**  
 インポートしたポリシーの状態を選択します。  
  
-   **[インポート時にポリシーの状態を保存します]**  
  
-   **[インポート時にすべてのポリシーを有効にします]**  
  
-   **[インポート時にすべてのポリシーを無効にします]**  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md)   
 [ポリシー ベースの管理ポリシーのインポート](import-a-policy-based-management-policy.md)   
 [ポリシーベースの管理ポリシーのエクスポート](export-a-policy-based-management-policy.md)  
  
  
