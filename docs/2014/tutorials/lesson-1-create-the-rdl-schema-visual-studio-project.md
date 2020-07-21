---
title: 'レッスン 1: RDL スキーマ Visual Studio プロジェクトを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c34062acefc2dfd847790a39cea35b03727f49ff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678520"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a>レッスン 1 : RDL スキーマ Visual Studio プロジェクトの作成
  このチュートリアルでは、簡単なコンソール アプリケーションを作成します。 このチュートリアルは、で[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]開発することを前提としています。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services で実行されているレポート サーバー Web サービスにアクセスする場合は、"_SQLExpress" を "ReportServer" パスに追加する必要があります。 次に例を示します。  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a>Web サービス プロキシを作成するには  
  
1.  [**スタート**] メニューから、[**すべてのプログラム**]、[Microsoft Visual Studio]、[ **Visual Studio Tools**]、[ **Visual Studio 2010 コマンドプロンプト**] の順に選択します。  
  
2.  C#: を使用している場合は、コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Visual Basic を使用している場合は、次のコマンドを実行します。  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     このコマンドは .cs ファイルまたは .vb ファイルを生成します。 このファイルをアプリケーションに追加します。  
  
### <a name="to-create-a-console-application"></a>コンソール アプリケーションを作成するには  
  
1.  [**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックして [**新しいプロジェクト**] ダイアログボックスを開きます。  
  
2.  左側のウィンドウの [**インストールされたテンプレート**] で、[ **Visual Basic** ] または [ **Visual C#** ] ノードをクリックし、展開された一覧からプロジェクトの種類のカテゴリを選択します。  
  
3.  [**コンソールアプリケーション**] プロジェクトの種類を選択します。  
  
4.  [**名前**] ボックスに、プロジェクトの名前を入力します。 名前`SampleRDLSchema`を入力します。  
  
5.  [**場所**] ボックスにプロジェクトを保存するパスを入力するか、[**参照**] をクリックしてフォルダーに移動します。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]ソリューションエクスプローラーに、プロジェクトの折りたたまれたビューが表示されます。  
  
7.  **[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。  
  
8.  生成した .cs ファイルまたは .vb ファイルの場所に移動し、ファイルを選択して、[**追加**] をクリックします。  
  
     また、Web 参照が動作するように、<xref:System.Web.Services> 名前空間への参照を追加する必要があります。  
  
9. [プロジェクト] メニューの **[参照の追加]** をクリックします。  
  
     [**参照の追加**] ダイアログボックスの [ **.net** ] タブで、[ **system.web. Services**] を選択し、[ **OK**] をクリックします。  
  
     レポートサーバー Web サービスに接続する方法の詳細については、「 [Web サービスと .NET Framework を使用したアプリケーションの構築](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)」を参照してください。  
  
10. ソリューションエクスプローラーで、プロジェクトノードを展開します。 プロジェクトには、Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) という既定の名前のコード ファイルが追加されていることがわかります。  
  
11. Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) ファイルを開き、次のコードに置き換えます。  
  
     次のコードは、読み込み、変更、保存の機能を実装するときに使用するメソッドの一部です。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a>次のレッスン  
 次のレッスンでは、XML スキーマ定義ツール (Xsd.exe) を使用して RDL スキーマからクラスを生成し、プロジェクトに組み込みます。 「[レッスン 2: Xsd ツールを使用して RDL スキーマからクラスを生成](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)する」を参照してください。  
  
## <a name="see-also"></a>参照  
 [RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
