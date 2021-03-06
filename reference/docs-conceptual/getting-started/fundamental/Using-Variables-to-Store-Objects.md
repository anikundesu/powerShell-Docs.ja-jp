---
ms.date: 2017-06-05
keywords: "PowerShell, コマンドレット"
title: "変数を使用したオブジェクトの保存"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a>変数を使用したオブジェクトの保存
PowerShell ではオブジェクトを操作します。 PowerShell では、変数 (本質的には名前付きのオブジェクト) を作成し、後で使用するために出力を保持できます。 他のシェルで変数を使用することに慣れている場合、PowerShell の変数はテキストではなくオブジェクトであることに注意してください。

変数は常に最初の文字が $ で指定され、名前には任意の英数字またはアンダースコアを含めることができます。

### <a name="creating-a-variable"></a>変数の作成
次のように有効な変数名を入力することで、変数を作成できます。

```
PS> $loc
PS>
```

**$loc** に値がないため、これは結果を返しません。 変数の作成と値の割り当てを同一の手順で行うことができます。 PowerShell では、変数の作成はその変数が存在しない場合にのみ行われます。存在する場合は、指定した値が既存の変数に割り当てられます。 変数 **$loc** に現在の場所を格納するには、次のように入力します。

```
$loc = Get-Location
```

このコマンドを入力しても出力は表示されません。出力が $loc に送られるためです。 PowerShell で出力が表示されるのは、他に行き先のないデータが決まって画面に送られることの副作用です。 $loc と入力することで現在の場所が表示されます。

```
PS> $loc

Path
----
C:\temp
```

**Get-Member** を使用して変数の内容に関する情報を表示できます。 $loc を Get-Member へパイプ処理すると、Get-Location からの出力と同様、これが **PathInfo** オブジェクトであることがわかります。

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>変数の操作
PowerShell には変数を操作するためのコマンドがいくつか用意されています。 次のように入力すると、完全な一覧が読みやすい形式で表示されます。

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

現在の PowerShell セッションで作成する変数に加えて、いくつかのシステム定義の変数があります。 **Remove-Variable** コマンドレットを使用して、PowerShell によって制御されない変数をすべてクリアできます。 すべての変数をクリアするには、次のコマンドを入力します。

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

これにより、以下に示される確認プロンプトが作成されます。

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

その後で **Get-Variable** コマンドレットを実行すると、残りの PowerShell 変数が表示されます。 変数 PowerShell ドライブもあるため、次のように入力してすべての PowerShell 変数を表示することもできます。

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Cmd.exe 変数の使用
PowerShell は Cmd.exe ではありませんが、コマンド シェル環境で実行され、Windows のあらゆる環境で使用できるものと同じ変数を使用できます。 これらの変数は **env** という名前のドライブを介して公開されます。 これらの変数を表示するには次のように入力します。

```
Get-ChildItem env:
```

標準的な変数コマンドレットは **env:** 変数を処理するよう設計されてはいませんが、**env:** プレフィックスを指定して引き続き使用することができます。 たとえば、PowerShell 内から次のように入力してコマンドシェル **%SystemRoot%** 変数を使用すると、オペレーティング システムのルート ディレクトリを表示できます。

```
PS> $env:SystemRoot
C:\WINDOWS
```

さらに、PowerShell 内から環境変数を作成および変更することもできます。 Windows PowerShell からアクセスされる環境変数は、Windows の他の場所の環境変数に適用される通常の規則に準拠しています。

