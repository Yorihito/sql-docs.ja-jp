---
title: '手順 3 : エラー フロー リダイレクトの追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5683a45d-9e73-4cd5-83ca-fae8b26b488c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e2c9e20ae26c3eec7069a20a09d54bd43836c0c9
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440459"
---
# <a name="step-3-adding-error-flow-redirection"></a>手順 3:エラー フロー リダイレクトの追加
  前の実習で学んだように、Lookup Currency Key 変換で壊れているサンプル フラット ファイルを処理しようとするとエラーが発生し、変換を行うことができません。 この変換ではエラー出力に既定の設定を使用するため、エラーが発生すると変換は失敗します。 変換が失敗すると、それ以降のパッケージも失敗します。  
  
 エラー出力を使用し、失敗した行を別の処理パスにリダイレクトするようにコンポーネントを構成することで、変換の失敗を回避できます。 別のエラー処理パスを使用すると、さまざまな処理が可能になります。 たとえば、データを消去した後に失敗した行を再処理できます。 失敗した行を詳細なエラー情報と共に保存し、後の検証や再処理に役立てることも可能です。  
  
 ここでは、失敗した行をエラー出力にリダイレクトするよう Lookup Currency Key 変換を構成します。 データ フローのエラー分岐では、失敗した行はファイルに書き込まれます。  
  
 既定では、エラー出力の2つの追加列 ( [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] **ErrorCode**と**errorcolumn**) には、エラー番号を表す数値コードと、エラーが発生した列の ID だけが含まれます。 これらの数値は、対応するエラー説明がないとあまり役に立ちません。  
  
 エラー出力の有用性を高めるには、パッケージによって失敗行がファイルに書き込まれる前に、スクリプト コンポーネントを使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API にアクセスし、エラーの説明を取得します。  
  
### <a name="to-configure-an-error-output"></a>エラー出力を構成するには  
  
1.  [ **SSIS ツールボックス**] で **[共通**] を展開し、[**スクリプトコンポーネント**] を [**データフロー** ] タブのデザイン画面にドラッグします。 [ **Lookup Currency Key** ] 変換の右側に**スクリプト**を配置します。  
  
2.  **[スクリプト コンポーネントの種類を選択]** ダイアログ ボックスで、 **[変換]** をクリックし、 **[OK]** をクリックします。  
  
3.  **[Lookup Currency Key]** 変換をクリックします。赤色の矢印を、新しく追加した **[スクリプト]** 変換までドラッグして、これら 2 つのコンポーネントを接続します。  
  
     赤い矢印は、 **[Lookup Currency Key]** 変換のエラー出力を表します。 赤い矢印を使用して変換をスクリプト コンポーネントに接続すると、エラー処理をスクリプト コンポーネントにリダイレクトできます。スクリプト コンポーネントではエラーが処理され、変換先に送信されます。  
  
4.  **[エラー出力の構成]** ダイアログ ボックスの **[エラー]** 列で、 **[行のリダイレクト]** を選択し、 **[OK]** をクリックします。  
  
5.  **[データ フロー]** デザイン画面で、新しく追加した **[スクリプト コンポーネント]** で **[スクリプト コンポーネント]** をクリックし、名前を「 **Get Error Description**」に変更します。  
  
6.  **[Get Error Description]** 変換をダブルクリックします。  
  
7.  **[スクリプト変換エディター]** ダイアログ ボックスの **[入力列]** ページで、 **[ErrorCode]** 列を選択します。  
  
8.  **[入力および出力]** ページで **[出力 0]** を展開し、 **[出力列]** をクリックして、 **[列の追加]** をクリックします。  
  
9. プロパティに `Name` 「 **ErrorDescription** 」と入力し、 `DataType` プロパティを**Unicode 文字列 [DT_WSTR]** に設定します。  
  
10. [**スクリプト**] ページで、 `LocaleID` プロパティが**英語 (米国**に設定されていることを確認します。  
  
11. **[スクリプトの編集]** をクリックして、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) を開きます。 `Input0_ProcessInputRow` メソッドに、次のコードを入力するか貼り付けます。  
  
     [Visual Basic]  
  
    ```  
    Row.ErrorDescription =   
      Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
    ```  
  
     [Visual C#]  
  
    ```  
    Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
    ```  
  
     完成したサブルーチンのコードは次のようになります。  
  
     [Visual Basic]  
  
    ```  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription =   
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
    ```  
  
     [Visual C#]  
  
    ```  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
        {  
  
            Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
        }  
    ```  
  
12. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックし、スクリプトをビルドして変更を保存し、VSTA を閉じます。  
  
13. **[OK]** をクリックして、 **[スクリプト変換エディター]** ダイアログ ボックスを閉じます。  
  
## <a name="next-steps"></a>次の手順  
 [手順 4: フラットファイル変換先の追加](lesson-4-4-adding-a-flat-file-destination.md  
  
  
