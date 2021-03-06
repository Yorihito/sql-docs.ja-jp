---
description: レコードセット内を移動する他の方法
title: レコードセット内の他の移動方法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- Recordset object [ADO], moving
- MovePrevious method [ADO]
ms.assetid: 9f8cf1b2-3def-453f-a0ff-4646c5f15262
author: rothja
ms.author: jroth
ms.openlocfilehash: e8c668bc24b388d0367429086416cd67b5355550
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980293"
---
# <a name="more-ways-to-move-in-a-recordset"></a>レコードセット内を移動する他の方法
次の4つの方法を使用して、 **レコードセット**、 [MoveFirst、MoveLast、MoveNext、および MovePrevious](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)を移動またはスクロールします。 (これらのメソッドの一部は、順方向専用カーソルでは使用できません)。  
  
 **MoveFirst** は、現在のレコードの位置をレコード **セット**内の最初のレコードに変更します。 **MoveLast** は、現在のレコードの位置を **レコードセット**内の最後のレコードに変更します。 **MoveFirst**または**MoveLast**を使用するには、**レコードセット**オブジェクトがブックマークまたは後方カーソル移動をサポートしている必要があります。それ以外の場合、メソッドの呼び出しでエラーが発生します。  
  
 **MoveNext** は、現在のレコードの位置を1つ前に移動します。 **MoveNext**を呼び出すときに最後のレコードを使用している場合、 **EOF**は**True**に設定されます。 **MovePrevious** は、現在のレコードの位置を1つ後ろに移動します。 **MovePrevious**を呼び出すときに最初のレコードを使用している場合、 **BOF**は**True**に設定されます。 次に示すように、これらのメソッドを使用するときに **EOF** プロパティと **BOF** プロパティをチェックし、 **レコードセット**のいずれかの端から移動すると、カーソルを有効な現在のレコード位置に戻すことができます。  
  
```  
. . .  
oRs.MoveNext  
If oRs.EOF Then oRs.MoveLast  
. . .   
```  
  
 または、 **MovePrevious** メソッドの場合は、次のようになります。  
  
```  
. . .   
oRs.MovePrevious  
If oRs.BOF Then oRs.MoveFirst  
. . .  
```  
  
 **レコードセット**がフィルター処理または並べ替えられていて、現在のレコードのデータが変更された場合、その位置も変更される可能性があります。 このような場合、 **MoveNext** メソッドは通常どおり動作しますが、位置が古い位置ではなく新しい位置から前方に移動されることに注意してください。 たとえば、レコードが並べ替えられたレコード**セット**の末尾に移動されるように、現在のレコードのデータを変更すると、 **MoveNext**を呼び出すと、ADO によって現在のレコードが**レコードセット**内の最後のレコードの後の位置 (**EOF**  =  **True**) に設定されます。  
  
 **レコードセット**オブジェクトのさまざまな Move メソッドの動作は、**レコードセット**内のデータによって、ある程度異なります。 **レコードセット**に追加された新しいレコードは、最初に特定の順序で追加されます。これは、データソースによって定義され、新しいレコード内のデータに対して暗黙的または明示的に依存する場合があります。 たとえば、 **レコードセット**を設定するクエリ内で並べ替えや結合が行われた場合、新しいレコードは **レコードセット**内の適切な場所に挿入されます。 **レコードセット**の作成時に順序が明示的に指定されていない場合、データソースの実装を変更すると、返された行の順序が誤って変更される可能性があります。 さらに、 **レコードセット** の並べ替え、フィルター処理、および編集関数は、順序に影響を与える可能性があり、場合によっては、レコードセット内の行が表示されます。  
  
 そのため、 **MoveNext**、 **MovePrevious**、 **MoveFirst**、 **MoveLast**、および **Move** はすべて、同じ **レコードセット**に対して実行される他の操作にも影響を受けます。 ADO は、明示的に移動するまでは常に現在の位置を維持しようとしますが、場合によっては、介在する変更によって、後続の移動の影響を理解するのが難しくなります。 たとえば、 **MoveFirst** を呼び出して、並べ替えられた **レコードセット** の最初の行の位置を確認し、並べ替えを昇順から降順に変更した場合は、同じ行に存在しますが、現在は **レコードセット**の最後の行になります。 **MoveFirst** では、別の行 (新しい最初の行) に移動します。  
  
 もう1つの例として、 **レコードセット** の途中の特定の行に位置していて、 **Delete** を呼び出してから **MoveNext**を呼び出すと、削除されたレコードの直後にあるレコードになります。 ただし、 **MovePrevious** を呼び出すと、レコード **セット**のアクティブなメンバーシップで削除されたレコードがカウントされなくなるため、現在のレコードを削除したレコードよりも前にレコードが作成されます。  
  
 現在のレコード内のデータを変更することによって、現在のレコードに対して **MovePrevious**、 **MoveNext**、および **移動** を行うメソッドに対して、すべてのプロバイダーに対して一貫性のある移動セマンティクスを定義することは特に困難です。 たとえば、並べ替えられたフィルター選択された **レコードセット**を使用しているときに、他のすべてのレコードの前に移動するように現在のレコードのデータを変更したが、変更されたデータがフィルターと一致しなくなった場合は、 **MoveNext** 操作がどのようになるかが明確ではありません。 最も安全な結論は、レコードの編集、追加、または削除中にデータが変更された場合に、 **レコードセット** 内の相対的な移動が危険 ( **MoveFirst** または **MoveLast**を使用するなど) よりも、絶対移動ではないということです。 並べ替えとフィルター処理は、主キーまたは ID に基づいて行う必要があります。この種類の値は変更しないようにしてください。