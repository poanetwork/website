---
description: Parity客户端可能需要更新以准备硬分叉
---

# Parity升级指南

{% hint style="info" %}
本指南假定您是从用于节点初始部署的同一台计算机上运行此脚本的。 您应该已经安装了`python`和`ansible`，并且具有正确的ssh密钥对以根访问该节点。
{% endhint %}

## 运行更新

1\) 如果尚未克隆poa-devops存储库，请克隆它

```text
git clone https://github.com/poanetwork/poa-devops.git
cd poa-devops
```

或获取最新更改

```text
cd poa-devops
git pull origin master
```

2\) 创建 `group_vars/all`文件：

```text
cp group_vars/upd-parity-version.example group_vars/all
```

并更改以下变量：

1. `poa_role` - 节点在网络上的角色 \(`bootnode`, `validator`, `moc`, `explorer` 之一\)
2. `GENESIS_BRANCH` - `"sokol"` 或 `"core"` 或 `"dai"` 或 `"kovan"`，具体取决于您要更新的网络

不要改变其他选项

3\) 创建/编辑`hosts`文件，并使用以下标头将您节点的ip地址（假设为192.0.2.1）放在其中：

```text
[upd-parity-version]
192.0.2.1
```

{% hint style="info" %}
如果要更新现有文件，请确保删除其他标签\[...\]和ips。
{% endhint %}

4\) 运行脚本（如有必要，将用户：ubuntu更改为您的用户名）：

```text
ansible-playbook -i hosts upd-parity-version.yml
```

{% hint style="warning" %}
如果遇到ssh连接错误，请尝试在上面的命令行中添加选项`-e 'ansible_ssh_user=ubuntu`'，用正确的ssh用户名替换ubuntu，根据用户的设置，该用户名通常为`ubuntu`或`root`或`poa`或`centos`。 您可能还需要使用`--key-file=/path/to/private.key` cli选项指定ssh私钥的确切路径。

如果要在本地计算机上安装更新，请使用`-c local`而不是指定私钥
{% endhint %}

## 验证更新

{% hint style="success" %}
Playbook运行应正确完成
{% endhint %}

1\) 打开网络统计网页：

* Sokol测试网络: [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network)
* Core核心网络: [https://core-netstat.poa.network](https://core-netstat.poa.network)
* Dai网络: [https://dai-netstat.poa.network](https://dai-netstat.poa.network)
* Kovan网络: [https://kovan-netstat.poa.network](https://kovan-netstat.poa.network)

检查您的节点是否为“绿色”并且正在捕获新的块。 完全启动并重新连接可能需要5到6分钟。

2\) 连接到节点

```text
ssh root@192.0.2.1
```

并检查奇偶校验版本（将引导节点`bootnode`替换为正确的角色名称，例如验证人`validator`）：

```text
/home/bootnode/parity --version
```

示例输出（版本号可能不同）：

```text
Parity Ethereum
  version Parity-Ethereum/v2.4.6-stable-94164e1-20190514/x86_64-linux-gnu/rustc1.34.1
Copyright 2015-2018 Parity Technologies (UK) Ltd.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

By Wood/Paronyan/Kotewicz/Drwięga/Volf
   Habermeier/Czaban/Greeff/Gotchac/Redmann
```

3\) 在第二天，在网络状态网页和相关功能上检查您节点的状态（例如，对于验证程序，是否仍从挖掘密钥向支付密钥发送块奖励？）。

## 回滚到以前的版本（如果有问题）

{% hint style="warning" %}
如果您遇到任何错误，请先咨询POA团队，可能您遇到的是小问题，无需回滚
{% endhint %}

1\) 连接到节点：

```text
ssh root@192.0.2.1
```

2\) 切换到主文件夹（用正确的角色名称替换引导节点`bootnode`）：

```text
cd /home/bootnode
```

3\) 停止服务：

```text
systemctl stop poa-netstats
systemctl stop poa-parity
```

4\) 找到备份文件夹：

```text
ls backups-version
```

它包含以格式创建备份的时间标记的文件夹`<year><month><day>T<hour><minute><second>`, 等等。

```text
# ls backups-version
20190311T200132 20190614T214517
```

复制对应于这一天的版本号。 在以下示例中，我们假设它是`20180209T214517`.

5\) 确保您拥有可用的挖掘密钥数据（密钥文件，密码，地址）

6\) 从新版本中删除文件：

```text
rm -rf parity_data
rm parity
rm node.toml
```

7\) 从备份中还原这些文件的先前版本（**在每行的结尾处请注意点`.`，它们很重要）**：

```text
cp -a backups-version/20190614T214517/parity .
cp -a backups-version/20190614T214517/parity_data .
cp -a backups-version/20180614T214517/node.toml .
```

8\) 检查parity版本（必须为先前版本）

```text
./parity --version
```

示例输出（版本号可能不同）

```text
Parity Ethereum
  version Parity-Ethereum/v2.3.2-beta-678138f-20190203/x86_64-linux-gnu/rustc1.31.1
Copyright 2015-2018 Parity Technologies (UK) Ltd.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

By Wood/Paronyan/Kotewicz/Drwięga/Volf
   Habermeier/Czaban/Greeff/Gotchac/Redmann
```

9\) 重新启动服务

```text
systemctl restart poa-parity
systemctl restart poa-netstats
```

10\) 打开网络统计网页：

* Sokol测试网络: [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network)
* Core核心网络: [https://core-netstat.poa.network](https://core-netstat.poa.network)
* Dai网络: [https://dai-netstat.poa.network](https://dai-netstat.poa.network)

检查您的节点是否为“绿色”并且正在捕获新的块。 完全启动并重新连接可能需要2-3分钟

