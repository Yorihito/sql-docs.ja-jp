---
title: スクリプト コンポーネントによる ODBC 変換先の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 065a7e0e85da8ad362db8a6160724eaf84971f84
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427119"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>スクリプト コンポーネントによる ODBC 変換先の作成
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、通常、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先および [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC を使用して、ODBC 変換先にデータを保存します。 ただし、単一のパッケージで使用するアドホックな ODBC 変換先を作成することもできます。 このアドホックな ODBC 変換先を作成するには、次の例に示すように、スクリプト コンポーネントを使用します。  
  
> [!NOTE]  
>  複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、このスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。 詳細については、「 [カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、既存の ODBC 接続マネージャーを使用して、データ フローのデータを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存する変換先コンポーネントの作成方法を示します。  
  
 この例は、「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で示したカスタムの [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先を変更したものです。 ただし、この例のカスタムの [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先は、ODBC 接続マネージャーを使用してデータを ODBC 変換先に保存するように変更されています。 こうした変更には、次の変更も含まれています。  
  
-   マネージド コードから ODBC 接続マネージャーの `AcquireConnection` メソッドを呼び出すことはできません。このメソッドを呼び出すと、ネイティブ オブジェクトが返されます。 そのため、この例では、接続マネージャーの接続文字列を使用して、マネージド ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーで直接データ ソースに接続しています。  
  
-   `OdbcCommand` には、位置パラメーターが必要です。 パラメーターの位置は、コマンドのテキストの疑問符 (?) で示されます (一方、`SqlCommand` では名前付きパラメーターが必要です)。  
  
 この例では、**AdventureWorks** サンプル データベースの **Person.Address** テーブルを使用します。 この例では、このテーブルの第1列と第4列、つまり**int * AddressID*** および**nvarchar (30) City**列をデータフローに渡します。 「[特定の種類のスクリプト コンポーネントの開発](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)」の変換元、変換、および変換先の例でも、同じデータが使用されます。  
  
#### <a name="to-configure-this-script-component-example"></a>このスクリプト コンポーネントの例を構成するには  
  
1.  **AdventureWorks** データベースに接続する ODBC 接続マネージャーを作成します。  
  
2.  **AdventureWorks** データベースで次の Transact-SQL コマンドを実行して、変換先テーブルを作成します。  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。  
  
4.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します (変換なしで直接変換元を変換先に接続することもできます)。このサンプルを機能させるには、上流コンポーネントの出力に、**AdventureWorks** サンプル データベースの **Person.Address** テーブルにある **AddressID** 列と **City** 列を最低限含める必要があります。  
  
5.  **[スクリプト変換エディター]** を開きます。 **[入力列]** ページで、**AddressID** 列と **City** 列を選択します。  
  
6.  **[入力および出力]** ページで、入力を **MyAddressInput** などのわかりやすい名前に変更します。  
  
7.  **[接続マネージャー]** ページで、ODBC 接続マネージャーを追加または作成し、**MyODBCConnectionManager** などのわかりやすい名前を付けます。  
  
8.  [**スクリプト**] ページで、[**スクリプトの編集**] をクリックし、次に示すスクリプトをクラスに入力し `ScriptMain` ます。  
  
9. スクリプト開発環境と **[スクリプト変換エディター]** を閉じ、サンプルを実行します。  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>関連項目  
 [スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
