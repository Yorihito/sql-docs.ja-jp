---
title: カスタム アセンブリ オブジェクトの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97ee8e554fa246848b64ebafb0961f35d65f15c9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63264723"
---
# <a name="initializing-custom-assembly-objects"></a>カスタム アセンブリ オブジェクトの初期化
  状況によっては、カスタム アセンブリ クラスのプロパティ値とフィールド値をインスタンス化する際、これらを初期化する必要があります。 初期化が必要になる可能性が最も高いのは、レポートのグローバル オブジェクト コレクションからカスタム クラスと値を使用する場合です。 そのためには、レポートの **Code** オブジェクトの **OnInit** メソッドをオーバーライドします。 **OnInit** にアクセスするには、レポート定義の **Code** 要素を使用します。 レポートで使用する予定のカスタム アセンブリのクラスのプロパティ値またはフィールド値を初期化する方法は 2 つあります。1 つは、**OnInit** を使用してクラスの新しいインスタンスを宣言し、作成する方法、もう 1 つは、**OnInit** を使用してパブリックに使用できるメソッドを呼び出す方法です。  
  
## <a name="global-object-collections-and-initialization"></a>グローバル オブジェクト コレクションと初期化  
 カスタム クラス変数を初期化するときは、 **Globals** および **User** の各コレクションを使用できます。 レポート ライフサイクルで、**OnInit** メソッドを呼び出す時点では、**Parameters**、**Fields** および **ReportItems** の各コレクションを使用できません。 共有コレクションの **Globals** または **User** を使用するには、**Report** オブジェクト参照を含める必要があります。 たとえば、レポートにアクセスしているユーザーの現在の言語に基づいてカスタム クラスを初期化する場合、**Code** 要素は次のようになります。  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 前述のように、クラスのプロパティ値とフィールド値を初期化する 1 つの方法は、オーバーライドされたコンストラクターを呼び出すことによってクラスを宣言し、その新しいインスタンスを作成することです。  
  
 カスタム アセンブリのクラスのプロパティ値とフィールド値を初期化するもう 1 つの方法は、**OnInit** メソッドから定義したパブリックに使用できるメソッドを呼び出すことです。 最初に、レポート定義ファイルのクラスのインスタンス名を追加する必要があります。 適切なアセンブリ参照とインスタンス名を追加した後は、初期化メソッドを呼び出して、クラスのプロパティ値とフィールド値を初期化できます。 **OnInit** メソッドは、次のようになります。  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 カスタム クラスのアセンブリ参照とインスタンス名を追加する方法の詳細については、「[レポートにアセンブリへの参照を追加する &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md)」を参照してください。  
  
 グローバル オブジェクト コレクションの詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポートでのカスタム アセンブリの使用](using-custom-assemblies-with-reports.md)  
  
  
