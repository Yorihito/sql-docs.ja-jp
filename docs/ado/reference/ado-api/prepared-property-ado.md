---
description: Prepared プロパティ (ADO)
title: 準備されたプロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
author: rothja
ms.author: jroth
ms.openlocfilehash: 9b5095432d283a2a0695d948de08a9f6b0ab25c5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773131"
---
# <a name="prepared-property-ado"></a>Prepared プロパティ (ADO)
コンパイルされたバージョンの [コマンド](./command-object-ado.md) を実行前に保存するかどうかを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **ブール**値を設定または返します。 **True**に設定されている場合は、コマンドの準備が必要であることを示します。  
  
## <a name="remarks"></a>解説  
 **Prepared**プロパティを使用して、[コマンド](./command-object-ado.md)オブジェクトの最初の実行前に、 [CommandText](./commandtext-property-ado.md)プロパティで指定されたクエリの準備済み (またはコンパイル済み) のバージョンをプロバイダーが保存するようにします。 これにより、コマンドの最初の実行が遅くなることがありますが、プロバイダーがコマンドをコンパイルすると、プロバイダーはその後の実行に対してコンパイルされたバージョンのコマンドを使用します。これにより、パフォーマンスが向上します。  
  
 プロパティが **False**の場合、プロバイダーはコンパイルされたバージョンを作成せずに **コマンド** オブジェクトを直接実行します。  
  
 プロバイダーがコマンドの準備をサポートしていない場合、このプロパティが **True**に設定されていると、エラーが返されることがあります。 プロバイダーがエラーを返さない場合は、単にコマンドを準備する要求を無視し、 **準備** されたプロパティを **False**に設定します。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Prepared プロパティの例 (VB)](./prepared-property-example-vb.md)   
 [Prepared プロパティの例 (VC++)](./prepared-property-example-vc.md)