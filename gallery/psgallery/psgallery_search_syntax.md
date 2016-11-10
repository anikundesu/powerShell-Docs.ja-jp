---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell,コマンドレット,ギャラリー"
ms.date: 2016-10-14
contributor: manikb
title: psgallery_search_syntax
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: bb42496bdc9794b8d33dc9869f33771a241d31db

---

# ギャラリー検索構文

PowerShell ギャラリーでは単語、フレーズ、キーワード表現を使用して検索結果を絞り込むテキスト検索ボックスが用意されています。

## キーワードで検索

    dsc azure sql

検索では、3 つのキーワードを含む関連ドキュメントを検索すると、最も効果的に一致ドキュメントが返されます。

## フレーズとキーワードを使用して検索

    "azure sql" deployment

引用符 ("") の間にフレーズを入力すると、個々のキーワードではなく、特定のフレーズの検索に変わります。
一致するドキュメントには通常、大文字と小文字のバリエーション (例: "Azure SQL" など) を含む "azure sql" そのままのフレーズを含み、また通常は 'deployment' という単語も含まれます。

## フィールドのフィルター処理

特定の項目 ID (または 'Id'、'id') を検索するか、検索語句の前にフィールド名を付けて他の特定のフィールドを検索します。

検索可能フィールドは現在、'Id'、'Version'、'Tags'、'Author'、'Owner'、'Functions'、'Cmdlets'、'DscResources'、'PowerShellVersion' です。

[ID とタイトルの間の違いは何ですか。 ID とは、コンソールで使用する名前です。 タイトルとは、検索結果の項目ページの上部に表示される内容です。]

## 例

    ID:"PSReadline"
    id:"AzureRM.Profile"

ID フィールドの "PSReadline" または "AzureRM.Profile" 項目をそれぞれ検索するとします。

    Id:"AzureRM.Profile"

ID フィールドで "AzureRM.Profile" のある項目を検索する別の方法です。

'Id' フィルターは部分文字列の一致のため、次のように検索した場合、

    Id:"azure"
    
'AzureRM.Profile' と 'Azure.Storage' のような結果が得られます。

また、1 つのフィールドで複数のキーワードを検索することもできます。 または、フィールドを組み合わせて一致させます。

    id:azure tags:intellisense
    id:azure id:storage

また、フレーズ検索も行うことができます。

    id:"azure.storage"


DSC タグのあるすべての項目を検索します。

    Tags:"DSC"

指定した関数のあるすべての項目を検索します。

    Functions:"Update-AzureRM"

指定したコマンドレットのあるすべての項目を検索します。
    
    Cmdlets:"Get-AzureRmEnvironment"

指定した DSC リソース名のあるすべての項目を検索します。

    DscResources:"xArchive"

指定した PowerShellVersion のあるすべての項目を検索します。

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


最後に、'commands' など、サポートされていないフィールドを使用すると、単に無視され、すべてのフィールドが検索されます。 そのため、次のクエリ

    commands:blobs storage
    
は次のクエリと同じものとして解釈されます。

    blobs storage




<!--HONumber=Oct16_HO2-->

