---
ms.date: 2017-10-16
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "構成の適用"
ms.openlocfilehash: 4285dbe04c9745ec2a859e479848da2881c18de0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="enacting-configurations"></a>構成の適用

>適用先: Windows PowerShell 4.0、Windows PowerShell 5.0

PowerShell Desired State Configuration (DSC) 構成を適用するには、プッシュ モードとプル モードの 2 つの方法があります。

## <a name="push-mode"></a>プッシュ モード

![プッシュ モード](images/pushModel.png "プッシュ モードのしくみ")

プッシュ モードは、[Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) コマンドレットを呼び出してターゲット ノードに構成を適用するユーザー アクティビティを示します。

構成を作成し、コンパイルした後、プッシュ モードで適用するには、[Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) コマンドレットを呼び出し、コマンドレットの -Path パラメーターを構成 MOF が配置されているパスに設定します。
たとえば、構成 MOF が `C:\DSC\Configurations\localhost.mof` にある場合は、`Start-DscConfiguration -Path 'C:\DSC\Configurations'` というコマンドを使用してローカル コンピューターに適用します。

> __注__: 既定では、DSC はバックグラウンド ジョブとして構成を実行します。 構成を対話的に実行するには、__-Wait__ パラメーターを指定して [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) を呼び出します。

## <a name="pull-mode"></a>プル モード

![プル モード](images/pullModel.png "プル モードのしくみ")

プル モードでは、プル クライアントはリモート プル サービスから Desired State Configuration を取得するように構成されます。
同様に、プル サービスは、DSC サービスをホストするようにセットアップされ、プル クライアントに必要な構成とリソースを使用してプロビジョニングされています。
それぞれのプル クライアントには、ノードの構成に対して定期的なコンプライアンス チェックを実行するイベントがスケジュールされています。
イベントが最初にトリガーされたとき、プル クライアント上のローカル構成マネージャー (LCM) によって、LCM で指定された構成を取得するためのプル サービスへの要求が行われます。
プル サービスにその構成が存在し、最初の検証チェックに合格した場合、構成はプル クライアントにダウンロードされ、LCM によって実行されます。

LCM はクライアントが構成に準拠しているかどうかを、LCM の **ConfigurationModeFrequencyMins** プロパティで指定された間隔で定期的にチェックします。
LCM はプル サービスで更新された構成を、LCM の **RefreshModeFrequency** プロパティで指定された間隔で定期的にチェックします。
LCM の構成の詳細については、「[ローカル構成マネージャーの構成](metaConfig.md)」を参照してください。

プル サービスをホストするための推奨ソリューションは、DSC クラウド サービスである [Azure Automation](https://azure.microsoft.com/en-us/services/automation/) です。
これはホスト型ソリューションであり、管理とレポートをグラフィカルに行い、管理を一元化できます。

Windows Server でのプル サービスのセットアップについては、「[DSC Web プル サーバーのセットアップ](pullServer.md)」を参照してください。
ただし、この実装では機能が制限されており、統合の一部を "ユーザー自身で" 行う必要があることに注意してください。

次のトピックでは、プル サービスとクライアントについて説明します。

- [Azure Automation DSC の概要](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Setting up an SMB pull server (SMB プル サーバーのセットアップ)](pullServerSMB.md)
- [Configuring a pull client (プル クライアントの構成)](pullClientConfigID.md)
