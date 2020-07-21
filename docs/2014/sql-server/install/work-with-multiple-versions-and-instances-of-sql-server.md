---
title: SQL Server の複数のバージョンおよびインスタンスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- concurrent installations [SQL Server]
- versions [SQL Server], multiple
- side-by-side installations [SQL Server]
- multiple SQL Server component versions
- installing SQL Server, side-by-side installations
- Setup [SQL Server], side-by-side installations
- 64-bit edition [SQL Server]
- 32-bit edition [SQL Server]
- editions [SQL Server], side-by-side installations
ms.assetid: 93acefa8-bb41-4ccc-b763-7801f51134e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76c0ec3da8661db4b7d132d27f5759d1d3571774
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041704"
---
# <a name="work-with-multiple-versions-and-instances-of-sql-server"></a>SQL Server の複数のバージョンおよびインスタンスの使用
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同じコンピューター上で [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の複数のインスタンスをサポートします。 また、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアップグレードしたり、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既にインストールされているコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールすることもできます。 サポートされるアップグレード シナリオについては、「 [サポートされるバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。  
  
## <a name="version-components-and-numbering"></a>バージョンのコンポーネントと番号付け  
 次に示す概念は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサイド バイ サイドのインスタンスでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の動作について理解するうえで役立ちます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の製品バージョンの標準の形式は MM.nn.bbbb.rr であり、各セグメントは次のように定義されています。  
  
 MM: メジャー バージョン  
  
 nn: マイナー バージョン  
  
 bbbb: ビルド番号  
  
 rr: ビルドのリビジョン番号  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、以前のバージョンと区別するために、メジャー リリースやマイナー リリースごとにバージョン番号を増加させています。 このバージョンに対する変更は、さまざまな目的に使用されます。 たとえば、ユーザー インターフェイスでのバージョン情報の表示、アップグレード時のファイルの置換方法の制御、およびサービス パックの適用に使用されることも、一連のバージョン間での機能の違いを区別するためのメカニズムとして使用されることもあります。  
  
### <a name="components-shared-by-all-versions-of-ssnoversion"></a>すべてのバージョンで共有されるコンポーネント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 特定のコンポーネントは、インストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのバージョンのすべてのインスタンスで共有されます。 同じコンピューターにバージョンが異なる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサイド バイ サイドでインストールすると、それらのコンポーネントは自動的に最新バージョンにアップグレードされます。 通常、このようなコンポーネントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最後のインスタンスがアンインストールされると自動的にアンインストールされます。  
  
 例 :[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser および Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer。  
  
### <a name="components-shared-across-all-instances-of-the-same-major-version-of-ssnoversion"></a>メジャー バージョンが同一の すべてのインスタンス間で共有されるコンポーネント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メジャー バージョンが同一ののバージョンでは、一部のコンポーネントをすべてのインスタンス間で共有します。 アップグレード時に共有コンポーネントが選択されると、既存のコンポーネントは最新バージョンにアップグレードされます。  
  
 例: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブック  
  
### <a name="components-shared-across-minor-versions"></a>マイナー バージョン間で共有されるコンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メジャー バージョンとマイナー バージョンが同一のバージョンでは、コンポーネントを共有していました。  
  
 例:セットアップ サポート ファイル。  
  
### <a name="components-specific-to-an-instance-of-ssnoversion"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに固有のコンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントまたはサービスには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに固有のものがあります。 これらは、インスタンス対応とも呼ばれます。 また、これらをホストしているインスタンスとバージョンが同じで、そのインスタンスにのみ使用されます。  
  
 例: [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
### <a name="components-that-are-independent-of-the-ssnoversion-versions"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンに依存しないコンポーネント  
 特定のコンポーネントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にインストールされますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバージョンに依存しません。 これらは、メジャー バージョン間で共有されたり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのバージョンで共有されたりすることがあります。  
  
 例 :Microsoft Sync Framework、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact。  
  
 Compact インストールの詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「インストール[ウィザードから SQL Server 2014 をインストールする」 &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact のアンインストール方法の詳細については、「[SQL Server の既存のインスタンスのアンインストール &#40;セットアップ&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)」を参照してください。  
  
## <a name="using-ssnoversion-side-by-side-with-previous-versions-of-ssnoversion"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と以前のバージョンの並列使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを既に実行しているコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールすることができます。 既定のインスタンスが既にコンピューターに存在する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は名前付きインスタンスとしてインストールする必要があります。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep では、以前のバージョンの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] と同じコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の準備済みインスタンスをサイド バイ サイドでインストールすることはサポートされていません。 たとえば、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスと共に [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の準備済みインスタンスをサイド バイ サイドで準備することはできません。 ただし、同じメジャー バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数の準備済みインスタンスを、同じコンピューターにサイド バイ サイドでインストールできます。 詳細については、「 [SysPrep を使用した SQL Server のインストールに関する注意点](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」を参照してください。  
>   
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Windows Server 2008 R2 Server Core SP1 を搭載するコンピューターに、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とサイド バイ サイドでインストールすることはできません。 Server Core インストールの詳細については、「 [Install SQL Server 2014 On Server core](../../database-engine/install-windows/install-sql-server-on-server-core.md)」を参照してください。  
  
 次の表に、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のサイド バイ サイドのサポートを示します。  
  
|の既存のインスタンス [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|サイド バイ サイドのサポート|  
|--------------------------------------------------|----------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (32 ビット)|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (32 ビット)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]|  
  
## <a name="preventing-ip-address-conflicts"></a>IP アドレス競合の回避  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスが [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のスタンドアロン インスタンスとサイド バイ サイドでインストールされている場合は、IP アドレスで TCP ポート番号が競合しないように注意してください。 競合は通常、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の 2 つのインスタンスが両方とも既定の TCP ポート (1433) を使用するように構成されている場合に発生します。 競合を回避するには、一方のインスタンスが既定以外の固定ポートを使用するように構成します。 通常、固定ポートの構成は、スタンドアロン インスタンスに対して行うのが最も簡単です。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で異なるポートが使用されるように構成すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスがノードのスタンバイに失敗した場合に、予期しない IP アドレス/TCP ポート競合によってインスタンスの起動がブロックされる問題を回避できます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](hardware-and-software-requirements-for-installing-sql-server.md)   
 [インストールウィザード &#40;セットアップから SQL Server 2014 をインストール&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [SQL Server 2014 へのアップグレード](../../database-engine/install-windows/upgrade-sql-server.md)   
 [SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [旧バージョンとの互換性](../../../2014/getting-started/backward-compatibility.md)   
 [アップグレード アドバイザーを使用したアップグレードの準備](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
  
