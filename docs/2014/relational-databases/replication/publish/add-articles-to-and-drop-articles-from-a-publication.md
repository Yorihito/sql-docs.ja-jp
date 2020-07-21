---
title: パブリケーションのアーティクルの追加および削除 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7af1cac1f3ee8ecc9cb79632f8a4ef1e66ec82f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85038181"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication-sql-server-management-studio"></a>パブリケーションでのアーティクルの追加または削除 (SQL Server Management Studio)
  パブリケーションの新規作成ウィザードでパブリケーションを作成する場合は、最初にアーティクルを追加します。 このウィザードの使用の詳細については、「[パブリケーションの作成](create-a-publication.md)」を参照してください。  
  
 パブリケーションが作成されたら、[**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスの [**アーティクル**] ページでアーティクルを追加および削除します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。 アーティクルの追加と削除に関する注意点については、「[既存のパブリケーションでのアーティクルの追加および削除](add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>パブリケーションの作成後にアーティクルを追加するには  
  
1.  [**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスの [**アーティクル**] ページで、[チェックボックスがオンになっている**オブジェクトのみを一覧に表示**する] チェックボックスをオフにします。 これにより、パブリケーション データベース内のパブリッシュされていないオブジェクトも表示されるようになります。  
  
2.  追加する各アーティクルの隣にあるチェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>アーティクルを削除するには  
  
1.  [**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスの [**アーティクル**] ページで、削除する各アーティクルの横にあるチェックボックスをオフにします。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [アーティクルの定義](define-an-article.md)   
 [データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md)  
  
  
