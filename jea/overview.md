---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "JEA, PowerShell, セキュリティ"
title: "Just Enough Administration の概要"
ms.openlocfilehash: a664a8ad44916f8112f7ef7bac145a54b83f126d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2017
---
<a id="just-enough-administration" class="xliff"></a>

# Just Enough Administration

Just Enough Administration (JEA) は、PowerShell で管理できるものすべてに対する委任された管理を有効にするセキュリティ テクノロジです。
JEA を使用すると、以下のことを実行できます。

- 通常のユーザーに代わって特権の必要な操作を実行する仮想アカウントまたはグループの管理されたサービス アカウントを活用することによって、**お使いのコンピューター上の管理者の数を減らします。**
- **ユーザーが実行できる操作を制限します**。ここでは、ユーザーが実行できるコマンドレット、関数、および外部コマンドを指定できます。
- トランスクリプションとログを使用して、**ユーザーの操作を把握します**。このトランスクリプションとログは、ユーザーがセッション中にどんなコマンドを実行したかを正確に示します。

**これが重要な理由:**

サーバーの管理に使用される高い特権を持つアカウントには、深刻なセキュリティ リスクがあります。
そのようなアカウントが攻撃者に狙われた場合、組織全体に[横展開の攻撃](http://aka.ms/pth)が始まります。
侵害されたアカウントがさらに多くのアカウントやリソースへのアクセスを与え、会社の機密情報の盗難に一歩近づき、サービス拒否攻撃などが始まります。

しかしながら、管理者特権を削除することは簡単なことではありません。
DNS ロールが Active Directory ドメイン コントローラーと同じコンピューターにインストールされるという一般的なシナリオについて考えてみてください。
DNS 管理者は、DNS サーバーでの問題を解決するためにローカル管理者特権が必要ですが、そのためには、これらの管理者を高い特権を持つ "Domain Admins" セキュリティ グループのメンバーにする必要があります。
この方法は、ドメイン全体への制御や、そのコンピューター上のすべてのリソースへのアクセス権を DNS 管理者に効果的に付与します。

JEA は*最小限の特権*の原則の導入を支援し、この問題の対処に役立ちます。
JEA を利用すると、DNS 管理者に管理エンドポイントを構成して、これらの管理者が作業を行うのに必要なすべての PowerShell コマンドにアクセスできるように、またそれ以外のことを実行できないように指定できます。
つまり、DNS 管理者に Active Directory への権限を付与しなくても、侵害された DNS キャッシュを修復したり、DNS サーバーを再起動したり、またはファイル システムを参照したり、潜在的に危険性なスクリプトを実行したりできる適切なアクセスを提供できます。
さらに、JEA セッションが一時的な特権仮想アカウントを使用するように構成されている場合、DNS 管理者は*管理者以外の*資格情報を使用してサーバーに接続できる一方で、一般的には管理者特権を必要とするコマンドも実行できます。
この機能により、幅広い特権が与えられたローカル/ドメイン管理者ロールからユーザーを削除し、代わりに、各コンピューターでユーザーに許可する操作を慎重に制御できます。

<a id="get-started-with-jea" class="xliff"></a>

## JEA の使用を開始する

現在、Windows Server 2016 か Windows 10 を実行しているあらゆるコンピューターで JEA の使用を開始できます。
JEA は、Windows Management Framework の更新プログラムがインストールしてある以前のオペレーティング システムでも実行できます。
JEA の使用要件、JEA エンドポイントの作成、使用、監査方法については、次のトピックをご覧ください。

- [前提条件](prerequisites.md) - JEA を使用するための環境の設定方法について説明します。
- [ロール機能](role-capabilities.md) - JEA セッションでユーザーに許可する操作を決定するロールの作成方法について説明します。
- [セッション構成](session-configurations.md) - ユーザーをロールにマッピングし、JEA ID を設定する JEA エンドポイントの構成方法について説明します。
- [JEA の登録](register-jea.md) - JEA エンドポイントを作成し、ユーザーがそれに接続できるようにします。
- [JEA の使用](using-jea.md) - JEA のさまざまな使用方法について説明します。
- [セキュリティの考慮事項](security-considerations.md) - JEA 構成オプションのセキュリティ ベスト プラクティスとその意味について確認します。
- [JEA の監査とレポート](audit-and-report.md) - JEA エンドポイントの監査とレポートの方法について説明します。

<a id="samples-and-dsc-resource" class="xliff"></a>

## サンプルと DSC のリソース

JEA 構成の例と JEA DSC リソースは [JEA GitHub リポジトリ](https://github.com/PowerShell/JEA)で確認できます。
