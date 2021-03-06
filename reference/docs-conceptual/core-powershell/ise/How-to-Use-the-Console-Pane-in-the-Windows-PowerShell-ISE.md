---
ms.date: 2017-06-05
keywords: "PowerShell, コマンドレット"
title: "Windows PowerShell ISE でコンソール ウィンドウを使用する方法"
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 59e97bbc12269d855c4f3715171636647d4cc634
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Windows PowerShell ISE でコンソール ウィンドウを使用する方法
Windows PowerShell Integrated Scripting Environment (ISE) のコンソール ウィンドウは、スタンドアロンの Windows PowerShell ISE コンソール ウィンドウとまったく同じ動作をします。

コンソール ウィンドウでコマンドを実行するには、コマンドを入力し、Enter キーを押します。 順番に実行する複数のコマンドを入力するには、コマンドとコマンドの間で SHIFT キーを押しながら ENTER キーを押します。 コマンドを入力する際の支援機能については、「[スクリプト ウィンドウとコンソール ウィンドウでタブ補完を使用する方法](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)」をご覧ください。

コマンドを停止するには、ツール バーで **[実行を中止]** をクリックするか、または CTRL + BREAK キーを押します。 コンテキストが明確な場合は、コマンドを停止するために CTRL + C キーを押すこともできます。 たとえば、現在のウィンドウでテキストが選択されている場合、CTRL + C キーはコピー操作にマップされます。

Windows PowerShell v3 以降で、出力ウィンドウがコンソール ウィンドウと結合されました。 これの利点は、スタンドアロンの Windows PowerShell コンソールと同様の動作になったことと、この 2 つが独立していたときに必要だった手順の違いが解消されたことです。 次の操作を行います。

- コンソール ウィンドウからテキストを選択してクリップボードにコピーし、他の任意のウィンドウに貼り付けます。 テキストを選択するには、出力ウィンドウでマウスをクリックし、マウス ボタンを押したまま、取り込みたいテキスト上をドラッグします。 また、**Shift** キーを押しながら方向キーを押して、テキストを選択することもできます。 その後、CTRL+ C キーを押すか、ツール バーの **[コピー]** アイコンをクリックします。

- 選択したテキストを現在のカーソル位置に貼り付けます。 ツール バーの **[貼り付け]** アイコンをクリックします。

- コンソール ウィンドウ内のすべてのテキストをクリアします。 コンソール ウィンドウをクリアするには、ツール バーの **[コンソール ウィンドウのクリア]** アイコンをクリックするか、コマンド **Clear-Host** またはそのエイリアスである **cls** を実行します。

## <a name="see-also"></a>参照
- [Windows PowerShell ISE の使用](Using-the-Windows-PowerShell-ISE.md)

