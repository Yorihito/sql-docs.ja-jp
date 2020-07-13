---
title: データベースのロックおよびロック解除 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544994"
---
# <a name="locking-and-unlocking-databases-xmla"></a>データベースのロックおよびロック解除 (XMLA)
  データベースのロックおよびロック解除を行うには、それぞれ XML for Analysis (XMLA) の[ロック](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)およびロック[解除](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)コマンドを使用します。 通常、他の XMLA コマンドは、実行時にコマンドを完了させる必要に応じて、自動的にオブジェクトをロック/ロック解除します。 データベースを明示的にロックまたはロック解除して、[バッチ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)コマンドなどの1つのトランザクション内で複数のコマンドを実行し、他のアプリケーションが書き込みトランザクションをデータベースにコミットするのを防ぐことができます。  
  
## <a name="locking-databases"></a>データベースのロック  
 `Lock` コマンドは、現在アクティブなトランザクションのコンテキスト内で、共有オブジェクトまたは排他的に使用されるオブジェクトをロックします。 オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、共有ロックと排他ロックの2種類がサポートされています。 でサポートされるロックの種類の詳細につい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ては、「 [Mode 要素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla)」を参照してください。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、データベースに対するロックだけが可能です。 [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)要素には、データベースへのオブジェクト参照が含まれている必要があり [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 `Object` 要素が指定されていない場合、またはデータベース以外のオブジェクトを `Object` 要素が参照している場合には、エラーが発生します。  
  
> [!IMPORTANT]  
>  `Lock` コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけです。  
  
 他のコマンドは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに対する `Lock` コマンドを暗黙的に発行します。 データベースからデータまたはメタデータを読み取るすべての操作 ( [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)メソッドや[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを実行する[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドなど) は、データベースの共有ロックを暗黙的に発行します。 データベース上のオブジェクトに対してデータまたはメタデータの変更をコミットするトランザクション [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ( `Execute` [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)コマンドを実行するメソッドなど) は、データベースに対する排他ロックを暗黙的に発行します。  
  
## <a name="unlocking-objects"></a>データベースのロック解除  
 `Unlock` コマンドは、現在アクティブなトランザクションのコンテキスト内で確立されたロックを解除します。  
  
> [!IMPORTANT]  
>  コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけ `Unlock` です。  
  
 すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。 現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;Lock 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [XMLA の &#40;要素のロックを解除&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
