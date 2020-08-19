---
description: CreateParameter メソッド (ADO)
title: CreateParameter メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bf45e2d458784972d7057e95878c9db3526ffac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444324"
---
# <a name="createparameter-method-ado"></a>CreateParameter メソッド (ADO)
指定したプロパティを使用して、新しい [Parameter](../../../ado/reference/ado-api/parameter-object.md) オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>戻り値  
 **パラメーター**オブジェクトを返します。  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 任意。 **パラメーター**オブジェクトの名前を含む**文字列**値です。  
  
 *Type*  
 任意。 **Parameter**オブジェクトのデータ型を示す[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)値です。  
  
 *方向*  
 任意。 **パラメーター**オブジェクトの型を指定する[parameterdirection 列挙](../../../ado/reference/ado-api/parameterdirectionenum.md)値。  
  
 *[サイズ]*  
 任意。 パラメーター値の最大長を文字数またはバイト数で指定する **Long 型** の値。  
  
 *Value*  
 任意。 **Parameter**オブジェクトの値を指定する**バリアント**です。  
  
## <a name="remarks"></a>解説  
 **Createparameter**メソッドを使用して、指定した名前、型、方向、サイズ、および値を使用して新しい**パラメーター**オブジェクトを作成します。 引数で渡す値は、対応する **パラメーター** プロパティに書き込まれます。  
  
 このメソッドは、 **Parameter**オブジェクトを[Command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの**Parameters**コレクションに自動的に追加しません。 これにより、 **パラメーター** オブジェクトをコレクションに追加したときに ADO によって検証される値を持つ追加のプロパティを設定できます。  
  
 *型*引数に可変長データ型を指定する場合は、**パラメーター**コレクションに追加する前に、*サイズ*引数を渡すか、**パラメーター**オブジェクトの[size](../../../ado/reference/ado-api/size-property-ado-parameter.md)プロパティを設定する必要があります。それ以外の場合は、エラーが発生します。  
  
 *型*引数に数値データ型 (**Adnumeric**または**adDecimal**) を指定する場合は、 [numericscale](../../../ado/reference/ado-api/numericscale-property-ado.md)プロパティと[Precision](../../../ado/reference/ado-api/precision-property-ado.md)プロパティも設定する必要があります。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Append および CreateParameter メソッドの例 (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append および CreateParameter メソッドの例 (VC + +)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append メソッド (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
