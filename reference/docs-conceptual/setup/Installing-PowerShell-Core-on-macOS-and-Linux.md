# <a name="installing-powershell-core-on-macos-and-linux"></a>macOS および Linux への PowerShell Core のインストール

[Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 25][fed25]、[Fedora 26][fed26]、[Arch Linux][arch]、[macOS 10.12][mac] に対応しています。

公式にサポートしていない Linux ディストリビューションの場合、[PowerShell AppImage][lai] を利用できます。 また、Linux [`tar.gz` アーカイブ][tar]で直接、PowerShell バイナリを展開できます。ただし、場合によっては、OS に基づいて依存関係を別の手順で設定する必要があります。

すべてのパッケージは GitHub [リリース][] ページにあります。 パッケージがインストールされたら、ターミナルから `pwsh` を実行します。

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>パッケージ リポジトリによるインストール - Ubuntu 14.04

Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。 この方法を使用することをお勧めします。

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。

### <a name="installation-via-direct-download---ubuntu-1404"></a>直接ダウンロードによるインストール - Ubuntu 14.04

[リリース][] ページから Ubuntu コンピューターに Debian パッケージ `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

次にターミナルで次を実行します。

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> `dpkg -i` は依存関係が満たされずに失敗しますが、次のコマンド `apt-get install -f` で解決され、PowerShell パッケージの構成が完了します。

### <a name="uninstallation---ubuntu-1404"></a>アンインストール - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>パッケージ リポジトリによるインストール - Ubuntu 16.04

Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。
この方法を使用することをお勧めします。

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。

### <a name="installation-via-direct-download---ubuntu-1604"></a>直接ダウンロードによるインストール - Ubuntu 16.04

[リリース][] ページから Ubuntu コンピューターに Debian パッケージ `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

次にターミナルで次を実行します。

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> `dpkg -i` は依存関係が満たされずに失敗しますが、次のコマンド `apt-get install -f` で解決され、PowerShell パッケージの構成が完了します。

### <a name="uninstallation---ubuntu-1604"></a>アンインストール - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>パッケージ リポジトリによるインストール - Ubuntu 17.04

Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。
この方法を使用することをお勧めします。

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。

### <a name="installation-via-direct-download---ubuntu-1704"></a>直接ダウンロードによるインストール - Ubuntu 17.04

[リリース][] ページから Ubuntu コンピューターに Debian パッケージ `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

次にターミナルで次を実行します。

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> `dpkg -i` は依存関係が満たされずに失敗しますが、次のコマンド `apt-get install -f` で解決され、PowerShell パッケージの構成が完了します。

### <a name="uninstallation---ubuntu-1704"></a>アンインストール - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>パッケージ リポジトリによるインストール - Debian 8

Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。
この方法を使用することをお勧めします。

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。

### <a name="installation-via-direct-download---debian-8"></a>直接ダウンロードによるインストール - Debian 8

[リリース][] ページから Debian コンピューターに Debian パッケージ `powershell_6.0.0-1.debian.8_amd64.deb` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

次にターミナルで次を実行します。

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> `dpkg -i` は依存関係が満たされずに失敗しますが、次のコマンド `apt-get install -f` で解決され、PowerShell パッケージの構成が完了します。

### <a name="uninstallation---debian-8"></a>アンインストール - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>パッケージ リポジトリによるインストール - Debian 9

Linux 向け PowerShell Core はパッケージ リポジトリに公開され、インストール (と更新) が簡単です。
この方法を使用することをお勧めします。

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo apt-get upgrade powershell` を使用する更新だけが必要になります。

### <a name="installation-via-direct-download---debian-9"></a>直接ダウンロードによるインストール - Debian 9

[リリース][] ページから Debian コンピューターに Debian パッケージ `powershell_6.0.0-1.debian.9_amd64.deb` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

次にターミナルで次を実行します。

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> `dpkg -i` は依存関係が満たされずに失敗しますが、次のコマンド `apt-get install -f` で解決され、PowerShell パッケージの構成が完了します。

### <a name="uninstallation---debian-9"></a>アンインストール - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> このパッケージは Oracle Linux 7 でも動作します。

### <a name="installation-via-package-repository-preferred---centos-7"></a>パッケージ リポジトリによるインストール (推奨) - CentOS 7

Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo yum update powershell` を使用する PowerShell の更新だけが必要になります。

### <a name="installation-via-direct-download---centos-7"></a>直接ダウンロードによるインストール - CentOS 7

[CentOS 7][] を使用して、[リリース][] ページから CentOS コンピューターに RPM パッケージ `powershell-6.0.0-1.rhel.7.x86_64.rpm` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

次にターミナルで次を実行します。

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

ダウンロードという中間の手順なしでも RPM をインストールできます。

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>アンインストール - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>パッケージ リポジトリによるインストール (推奨) - Red Hat Enterprise Linux (RHEL) 7

Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

スーパーユーザーとして Microsoft リポジトリを一度登録すれば、その後は `sudo yum update powershell` を使用する PowerShell の更新だけが必要になります。

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>直接ダウンロードによるインストール - Red Hat Enterprise Linux (RHEL) 7

[リリース][] ページから Red Hat Enterprise Linux コンピューターに RPM パッケージ `powershell-6.0.0-1.rhel.7.x86_64.rpm` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

次にターミナルで次を実行します。

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

ダウンロードという中間の手順なしでも RPM をインストールできます。

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>アンインストール - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **注記:** PowerShell Core のインストール時、OpenSUSE に `libcurl` を提供するものがないという報告が表示されることがあります。
`libcurl` は、サポートされているバージョンの OpenSUSE に既にインストールされているはずです。
`zypper search libcurl` を実行して確定します。
エラーには 2 つの 'ソリューション' が提示されます。 'Solution 2' を選び、PowerShell Core のインストールを続行します。

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>パッケージ リポジトリによるインストール (推奨) - OpenSUSE 42.2

Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>直接ダウンロードによるインストール - OpenSUSE 42.2

[リリース][] ページから OpenSUSE コンピューターに RPM パッケージ `powershell-6.0.0-1.rhel.7.x86_64.rpm` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

ダウンロードという中間の手順なしでも RPM をインストールできます。

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>アンインストール - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>パッケージ リポジトリによるインストール (推奨) - Fedora 25

Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a>直接ダウンロードによるインストール - Fedora 25

[リリース][] ページから Fedora コンピューターに RPM パッケージ `powershell-6.0.0-1.rhel.7.x86_64.rpm` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

次にターミナルで次を実行します。

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

ダウンロードという中間の手順なしでも RPM をインストールできます。

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>アンインストール - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>パッケージ リポジトリによるインストール (推奨) - Fedora 26

Linux 向け PowerShell Core は公式 Microsoft リポジトリに公開され、インストール (と更新) が簡単です。

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-26"></a>直接ダウンロードによるインストール - Fedora 26

[リリース][] ページから Fedora コンピューターに RPM パッケージ `powershell-6.0.0-1.rhel.7.x86_64.rpm` をダウンロードします。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

次にターミナルで次を実行します。

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

ダウンロードという中間の手順なしでも RPM をインストールできます。

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>アンインストール - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

PowerShell は [Arch Linux][] User Repository (AUR) から入手できます。

* [タグが付けられた最新のリリース][arch-release]でコンパイルできます
* [最新のコミットからマスターに][arch-git]コンパイルできます
* [最新のリリース バイナリ][arch-bin]でインストールできます

AUR のパッケージはコミュニティにより保守管理されています。公式のサポートはありません。

AUR からパッケージをインストールする方法については、[Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) かコミュニティ [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) をご覧ください。

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

最近の Linux ディストリビューションを利用し、[リリース][] ページから Linux コンピューターに AppImage `powershell-6.0.0-x86_64.AppImage` をダウンロードします。

次にターミナルで次を実行します。

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

[AppImage][] では、インストールしなくても PowerShell を実行できます。 これは PowerShell とその依存関係 (.NET Core のシステム依存関係を含む) を 1 つのまとまったパッケージにバンドルする移植可能なアプリケーションです。 このパッケージはユーザーの Linux ディストリビューションに依存せずに動作し、1 つのバイナリです。

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Homebrew によるインストール (preferred) - macOS 10.12

[Homebrew][brew] は、macOS で足りないパッケージを管理します。 `brew` コマンドが見つからない場合、[指示][brew]に従い、Homebrew をインストールする必要があります。

Homebrew をインストールすると、PowerShell のインストールが簡単になります。 最初に [Homebrew-Cask][cask] をインストールします。その後、たくさんのパッケージをインストールできます。

```sh
brew tap caskroom/cask
```

これで PowerShell をインストールできます。

```sh
brew cask install powershell
```

新しいバージョンの PowerShell がリリースされたら、Homebrew の式を更新し、PowerShell をアップグレードしてください。

```sh
brew update
brew cask reinstall powershell
```

> 注: [Cask のこの問題](https://github.com/caskroom/homebrew-cask/issues/29301)に起因し、現在のところ、アップグレードには再インストールが必要になります。

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>直接ダウンロードによるインストール - macOS 10.12

macOS 10.12 を利用し、[リリース][] ページから macOS コンピューターに PKG パッケージ `powershell-6.0.0-osx.10.12-x64.pkg` をダウンロードします。

ファイルをダブルクリックして画面の指示に従うか、ターミナルからインストールします。

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>アンインストール - macOS 10.12

Homebrew で PowerShell をインストールした場合、アンインストールが簡単になります。

```sh
brew cask uninstall powershell
```

直接ダウンロードで PowerShell をインストールした場合、手動で PowerShell を削除する必要があります。

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

追加の PowerShell パス (ユーザー プロファイル パスなど) をアンインストールするには、このドキュメントの「[パス][paths]」セクションを参照し、`sudo rm` でパスを削除してください。 (注: Homebrew でインストールした場合、これは不要です。)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>インストール

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>最新の Kali (Kali GNU/Linux Rolling) でインストールせずに PowerShell を実行する

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>アンインストール - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

現在のところ、PowerShell は Raspbian Stretch でのみサポートされています。

### <a name="installation"></a>インストール

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>アンインストール - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>バイナリ アーカイブ

macOS プラットフォームと Linux プラットフォームで高度な展開シナリオを実行するために、PowerShell バイナリ `tar.gz` アーカイブが用意されています。

### <a name="dependencies"></a>依存関係

Linux の場合、PowerShell はすべての Linux ディストリビューションに移植可能なバイナリをビルドします。
ただし、.NET Core ランタイムはディストリビューションごとに異なる依存関係を必要とします。PowerShell でも同じです。

次の表は、公式にサポートされている Linux ディストリビューションと .NET Core 2.0 の依存関係をまとめたものです。

| OS                 | 依存関係 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind、libcurl、openssl-libs、libicu |
| Fedora 26          | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

公式にサポートされていない Linux ディストリビューションで PowerShell バイナリを展開するには、別の手順で、ターゲット OS に必要な依存関係をインストールする必要があります。 たとえば、[Amazon Linux dockerfile][amazon-dockerfile] は依存関係を先にインストールし、それから Linux `tar.gz` アーカイブを抽出します。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>インストール - バイナリ アーカイブ

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>アンインストール - バイナリ アーカイブ

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>パス

* `$PSHOME` は `/opt/microsoft/powershell/6.0.0/` です
* ユーザー プロファイルは `~/.config/powershell/profile.ps1` から読み込まれます
* 既定のプロファイルは `$PSHOME/profile.ps1` から読み込まれます
* ユーザー モジュールは `~/.local/share/powershell/Modules` から読み込まれます
* 共有モジュールは `/usr/local/share/powershell/Modules` から読み込まれます
* 既定のモジュールは `$PSHOME/Modules` から読み込まれます
* PSReadline 履歴は `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` に記録されます

プロファイルは PowerShell のホスト別構成を順守します。そのため、既定のホスト固有プロファイルは同じ場所の `Microsoft.PowerShell_profile.ps1` にあります。

Linux と macOS では、[XDG Base Directory Specification][xdg-bds] を順守します。

macOS は BSD から派生しているため、`/opt` ではなく、`/usr/local` がプレフィックスとして使用されます。 そのため、`$PSHOME` は `/usr/local/microsoft/powershell/6.0.0/` です。シンボリックリンクは `/usr/local/bin/pwsh` にあります。

[リリース]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
