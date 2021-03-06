---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, PowerShell, セットアップ"
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>構成における同一重複リソースの許容

DSC は、構成内で競合するリソース定義を許可せず、処理しません。 競合を解決するのではなく、ただの失敗となります。 複合リソースなどの間で構成の再利用が多く行われるようになるほど、競合は頻繁に発生します。 競合するリソース定義が一致する場合、DSC は賢くこれを許可します。 このリリースにより、同一の定義を持つ複数のリソース インスタンスをサポートするようになりました:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

以前のリリースでは、'Web サーバー' ロールが確実にインストールされるようにするために発生する WindowsFeature FE_IIS と WindowsFeature Worker_IIS インスタンス間の競合により、コンパイルの失敗に終わっていました。 構成が実行される*すべて*のプロパティは、これら 2 つの構成間で一致していることに注目してください。 これらの 2 つのプロパティのリソースは*すべて*一致するため、結果として正常にコンパイルできるようになりました。 

2 つのリソース間でいずれかのプロパティが異なる場合、一致していないと見なされ、コンパイルは失敗します:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

この非常に類似した構成は、WindowsFeature FE_IIS と WindowsFeature Worker_IIS リソースが一致せず、競合が発生するようになったため、失敗します。

