---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, PowerShell, 構成, セットアップ"
title: "ノードの相互依存関係の指定"
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a>ノードの相互依存関係の指定

> 適用先: Windows PowerShell 5.0

DSC には、**WaitForAll**、**WaitForAny**、**WaitForSome** などの特別なリソースが用意されています。このリソースを構成で使用すると、他のノードの構成への依存関係を指定することができます。 これらのリソースの動作は次のとおりです。

* **WaitForAll**: **NodeName** プロパティで定義されているすべてのターゲット ノードで、指定されたリソースが目的の状態である場合に成功します。
* **WaitForAny**: **NodeName** プロパティで定義されているターゲット ノードの少なくとも 1 つで、指定されたリソースが目的の状態である場合に成功します。
* **WaitForSome**: **NodeName** プロパティのほか、**NodeCount** プロパティも指定します。 リソースは、**NodeName** プロパティで定義されたノードの最小数 (**NodeCount** で指定) で目的の状態になった場合に成功します。 

## <a name="using-waitforxxxx-resources"></a>WaitForXXXX リソースの使用

**WaitForXXXX** リソースを使用するには、待機する DSC リソースとノードを指定する、そのリソースの種類のリソース ブロックを作成します。 その後、構成の他のリソース ブロックで **DependsOn** プロパティを使用して、**WaitForXXXX** ノードで指定されている条件が成功するのを待ちます。

たとえば、次の構成では、ターゲット ノードは **MyDC** ノード上の **xADDomain** リソースが完了するまで 15 秒間隔で最大 30 回試行しながら待機した後、ドメインに参加できるようになります。

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**注:** 既定では、WaitForXXX リソースは 1 回試行してから失敗します。 これは必須ではありませんが、通常は、再試行の間隔と回数を指定することをお勧めします。

## <a name="see-also"></a>参照
* [DSC 構成](configurations.md)
* [DSC リソース](resources.md)
* [ローカル構成マネージャーの構成](metaConfig.md)

