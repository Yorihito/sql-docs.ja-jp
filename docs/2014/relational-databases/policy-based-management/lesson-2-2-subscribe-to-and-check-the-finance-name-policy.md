---
title: Finance の名前ポリシーのサブスクライブおよび確認 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e0c859bdd982fa7de586c9230754c571eb750944
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061615"
---
# <a name="subscribe-to-and-check-the-finance-name-policy"></a>Finance の名前ポリシーのサブスクライブおよび確認
  ここでは、Finance データベースを構成し、Finance ポリシー カテゴリをサブスクライブします。 その後で、Finance の名前ポリシーをテストします。  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a>Finance ポリシー カテゴリをサブスクライブするには  
  
1.  オブジェクトエクスプローラーで、[**データベース**] を展開し、を右クリックし `Finance` て [**ポリシー**] をポイントし、[**カテゴリ**] をクリックします。  
  
2.  カテゴリの [**サブスクライブ**済み] チェックボックスをオンにし `Finance` ます。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a>Finance の名前ポリシーの適用をテストするには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でクエリ ウィンドウを開きます。 **Finance の名前** ポリシーに違反するテーブルの作成を試みる次のステートメントを実行します。 このテーブルは、テーブル名が文字列 **fintbl**で始まっていないため、ポリシーに違反します。  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     ポリシーにより、テーブルの作成が防止され、ポリシー名を含む情報メッセージが返されます。  
  
2.  有効な名前を指定するには、コードを次のように変更し、ステートメントを再度実行します。  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     今度はテーブルが作成されます。  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a>ポリシーをサーバー全体に適用するには  
  
1.  現在、Finance ポリシー カテゴリをサブスクライブするのは Finance データベースだけです。 多くの場合、ポリシー カテゴリをサーバー全体に適用する方が簡単です。 オブジェクト エクスプローラーで **[管理]** を展開し、 **[ポリシー管理]** を右クリックして、 **[カテゴリの管理]** をクリックします。  
  
2.  **[ポリシー カテゴリの管理]** ダイアログ ボックスで Finance カテゴリを探し、Finance カテゴリの **[データベースのサブスクリプションの要求]** チェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] これで Finance カテゴリがすべてのデータベースに適用されるようになります。ただし、作成した条件により、Finance の名前ポリシーは Finance データベースにのみ適用されることになります。 これは、条件を複雑に組み合わせることで、多数のサーバーに対して適切な方法でポリシーを適用できるということを示しています。  
  
## <a name="summary"></a>まとめ  
 このチュートリアルでは、ポリシー ベースの管理の条件、ポリシー、およびポリシー グループを作成する方法と、フィルターを適用してポリシー ベースの管理対象がポリシーに準拠しているかどうかを調べる方法について学習しました。  
  
## <a name="next"></a>次へ  
 このチュートリアルはこれで終了です。 最初に戻るには、「 [チュートリアル: ポリシー ベースの管理を使用したサーバーの管理](tutorial-administering-servers-by-using-policy-based-management.md)」をクリックしてください。  
  
 チュートリアルの一覧については、 [SQL Server 2014 のチュートリアル](../../tutorials/tutorials-for-sql-server-2014.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md)  
  
  
