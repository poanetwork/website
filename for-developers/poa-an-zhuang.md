---
description: 运行一个完整的节点，同步到POA网络的区块链。
---

# POA安装

{% hint style="info" %}
您无需运行自己的节点即可与POA区块链进行交互（玩游戏，发送和接收资金以及使用DApp）。 可以将运行节点视为一项公共服务，它有益于链的分散化和整体安全性，并允许您使用自己的实例确认链的状态。
{% endhint %}

## 要求条件

* [Parity Ethereum client](https://github.com/paritytech/parity-ethereum/releases)
* [Modifications to spec.json file](https://github.com/poanetwork/poa-chain-spec/) \(在POA Github源\)

## 1\) 安装Parity

### 带有Homebrew单行二进制安装的Ubuntu / Debian和MacOS

比从源构建更快，但没有最先进的功能。

如果要从[源代码](https://github.com/paritytech/parity)构建或下载二进制版本，请参见官方的[Parity版本页面](https://github.com/paritytech/parity/releases)。 请使用稳定的`Parity`版本（1.11.8或更高版本）。

1\) 打开bash终端并在下面输入命令，如果客户端需要更新，只需再次运行该命令即可。

```text
bash <(curl https://get.parity.io -kL)
```

这将为您安装和配置Parity客户端。 在Ubuntu上，该脚本还将提供安装Netstats客户端并将其连接到ethstats.net的功能。 如果计划仅将`Parity`用于POA，则无需安装额外的软件。

### 从Linux发行版Snap Service安装

```text
sudo snap install parity --edge
```

### 在Windows上安装Parity

Windows上的Parity既可以作为系统服务安装，也可以从文件夹执行。 从“[Parity的发行版](https://github.com/paritytech/parity/releases)”页面中选择所需的可执行文件。 要在Windows上使用`Parity`连接到POA网络，请遵循下面的相应部分。

## 2\) 与POA网络连接并同步

### 在Parity上将Linux / MacOS连接到POA网络

从POA Github获取[spec.json](https://github.com/poanetwork/poa-chain-spec/blob/core/spec.json)和[bootnodes.txt](https://github.com/poanetwork/poa-chain-spec/blob/core/bootnodes.txt)文件。

{% hint style="info" %}
对于POA Sokol Testnet测试网络，在Github上选择适当的分支**branch**。
{% endhint %}

**1\) 克隆适当的Github库**

核心网络Core\(live\) network

```text
git clone -b core https://github.com/poanetwork/poa-chain-spec.git
```

测试网络Sokol\(test\) network

```text
git clone -b sokol https://github.com/poanetwork/poa-chain-spec.git
```

2\) 在终端运行

```text
parity --chain /path/to/spec.json --reserved-peers /path/to/bootnodes.txt ui
```

如果您想限制或选择特定的引导节点，请运行

```text
parity --chain /path/to/spec.json --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT ui
```

输入所需网络的所有提供的enodes，以逗号分隔，无空格。

### 将Windows计算机连接到Parity上的POA网络

从POA Github获取[spec.json](https://github.com/poanetwork/poa-chain-spec/blob/core/spec.json)和[bootnodes.txt](https://github.com/poanetwork/poa-chain-spec/blob/core/bootnodes.txt)文件。

{% hint style="info" %}
对于POA Sokol Testnet测试网络，在Github上选择适当的分支**branch。**
{% endhint %}

**1\)** 使用Git Bash输入以下命令

核心网络Core\(live\) network

```text
git clone -b core https://github.com/poanetwork/poa-chain-spec.git
```

测试网络Sokol\(test\) network

```text
git clone -b sokol https://github.com/poanetwork/poa-chain-spec.git
```

2\) 打开Windows命令提示符CMD或Windows Powershell，然后导航到`Parity`执行文件。

```text
parity --chain c:\path\to\spec.json --reserved-peers c:\path\to\bootnodes.txt ui
```

如果您想限制或选择特定的引导节点，请运行

```text
parity --chain c:\path\to\spec.json --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT ui
```

输入所需网络的所有提供的enodes，以逗号分隔，无空格。 

## 3\) 连接到您的节点

您可以使用以太坊的JSON-RPC或JavaScript控制台：[https://wiki.parity.io/Basic-Usage](https://wiki.parity.io/Basic-Usage)

不推荐使用Parity的UI，但是该站点上的信息提供了本地Parity Ethereum节点的替代方案：[https://wiki.parity.io/Parity-Wallet](https://wiki.parity.io/Parity-Wallet)

