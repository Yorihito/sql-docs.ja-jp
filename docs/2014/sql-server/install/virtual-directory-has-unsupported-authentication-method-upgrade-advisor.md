---
title: 仮想ディレクトリにサポートされていない認証方法がある (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3394181111267c01e9baaa13bd1b6d64339dd5eb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054645"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>仮想ディレクトリにサポートされていない認証方法がある (アップグレード アドバイザー)
  アップグレード アドバイザーによって、レポート マネージャー仮想ディレクトリまたはレポート サーバー仮想ディレクトリで、サポートされていない認証方法が検出されました。 アップグレードでサポートされていない認証方法には、匿名、ダイジェスト、および .NET Passport があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 セットアップでは、次のいずれかの認証方法を使用する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールをアップグレードすることはできません。  
  
-   Anonymous  
  
-   ダイジェスト  
  
-   .NET Passport  
  
 続行するには、インターネット インフォメーション サービス (IIS) の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに指定されている認証方法を変更するか、インストールを移行します。 インストールの移行の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードを続行するには、ReportServer および Reports の各仮想ディレクトリに対する IIS の認証方法を変更します。 IIS の認証方法を変更する方法については、IIS のマニュアルを参照してください。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに対する認証方法を変更した後、アップグレード アドバイザーを再実行して、アップグレードに関する問題がその他にないことを確認します。  
  
## <a name="see-also"></a>参照  
 [アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
