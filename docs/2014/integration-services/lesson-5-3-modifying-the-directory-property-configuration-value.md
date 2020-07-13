---
title: '手順 3 : Directory プロパティの構成値の変更 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a71a7a181322d60caca98da4ddf3261cbce99c9e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440369"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a>手順 3:Directory プロパティの構成値の変更
  ここでは、SSISTutorial.dtsConfig ファイルに保存されている構成設定のうち、パッケージ レベル変数 `User::varFolderName`の Value プロパティを変更します。 この変数は、ForEach ループ コンテナーの Directory プロパティを更新します。 変更後の値は、 `New Sample Data` 前のタスクで作成したフォルダーを指します。 構成設定を変更し、パッケージを実行すると、パッケージ レベル変数によって Directory プロパティが更新されます。この更新では、パッケージにもともと構成されていた Directory 値は使用されず、構成ファイルから生成された値が使用されます。  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Directory プロパティの構成設定を変更するには  
  
1.  前の実習でパッケージ構成ウィザードを使用して作成した SSISTutorial.dtsConfig 構成ファイルを探し、メモ帳などのテキスト エディターで開きます。  
  
2.  **ConfiguredValue**要素の値を、 `New Sample Data` 前のタスクで作成したフォルダーのパスと一致するように変更します。 パスは引用符で囲まないでください。 `New Sample Data`フォルダーがドライブのルートレベルにある場合 (C: など \\ )、更新された XML は次の例のようになります。  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     もちろん、ファイルの見出し情報、、 `GeneratedBy` `GeneratedFromPackageID` 、および作成**日**は異なります。 `Configuration` 要素に注目してください。 変数の `Value` プロパティである `User::varFolderName` に、C:\New Sample Data が含まれています。  
  
3.  変更を保存し、テキスト エディターを閉じます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 4:レッスン 5 のチュートリアル パッケージのテスト](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
