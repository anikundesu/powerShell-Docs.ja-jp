---
ms.date: 2017-06-05
keywords: "PowerShell, コマンドレット"
title: "ISEFile オブジェクト"
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a>ISEFile オブジェクト
  **ISEFile** オブジェクトは、Windows PowerShell® Integrated Scripting Environment (ISE) のファイルを表します。 これは Microsoft.PowerShell.Host.ISE.ISEFile クラスのインスタンスです。 このトピックでは、そのメンバー メソッドとメンバー プロパティについて説明します。 **$PsISE.CurrentFile** と、PowerShell タブのファイル コレクション内のファイルは、Microsoft.PowerShell.Host.ISE.ISEFile クラスのすべてのインスタンスです。

## <a name="methods"></a>メソッド

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 ファイルをディスクに保存します。

 **\[saveEncoding\]** - 省略可能な [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)。保存したファイルで使用する省略可能な文字エンコード パラメーター。 既定値は **UTF8** です。

 **例外**
 -   **System.IO.IOException**: ファイルを保存できませんでした。

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 指定したファイル名およびエンコードでファイルを保存します。

 **filename** - ファイルを保存するために使用する名前の文字列。

 **\[saveEncoding\]** - 省略可能な [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)。保存したファイルで使用する省略可能な文字エンコード パラメーター。 既定値は **UTF8** です。

 **例外**
 -   **System.ArgumentNullException**: **filename** パラメーターが null です。

- **System.ArgumentException**: **filename** パラメータが空です。

- **System.IO.IOException**: ファイルを保存できませんでした。

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>プロパティ

### <a name="displayname"></a>表示名
  Windows PowerShell ISE 2.0 以降でサポートされています。

 このファイルの表示名が含まれている文字列を取得する読み取り専用のプロパティ。 名前は、エディターの上部の **[ファイル]** タブに表示されます。 名前の末尾のアスタリスク \(\*\) は、保存されていない変更がファイルに含まれていることを示します。

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Editor
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 指定したファイルで使用される[エディター オブジェクト](The-ISEEditor-Object.md)を取得する読み取り専用のプロパティ。

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>エンコード
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 元のファイル エンコードを取得する読み取り専用のプロパティ。 これは **System.Text.Encoding** オブジェクトです。

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 開いているファイルの完全パスを指定する文字列を取得する読み取り専用プロパティ。

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 ファイルが最後に変更された後にファイルが保存されている場合に **$true** を返す読み取り専用のブール型プロパティ。

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  Windows PowerShell ISE 2.0 以降でサポートされています。 

 ファイルにタイトルが指定されたことがない場合に **$true** を返す読み取り専用のプロパティ。

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>参照
- [The ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [Windows PowerShell ISE スクリプト オブジェクト モデル](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE オブジェクト モデル リファレンス](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [ISE オブジェクト モデルの階層](The-ISE-Object-Model-Hierarchy.md)
