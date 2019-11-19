# 使用部署手册配置节点

要运行剧本，您将需要服务器上具有`sudo`特权且可以通过SSH公钥登录的用户。 默认情况下，假定此用户称为`ubuntu`。 如果您已经有一个满足以下要求的不同名称的用户，请在-hosts:all部分的`site.yml`前面将行`user:ubuntu`更改为您拥有的`sudo`用户

```text
---
- hosts: all
  user: ubuntu
  become: True
...
```

{% hint style="info" %}
脚本还将另外创建一个新的非特权用户，名为`Validator`，并将您的ssh公钥添加到`root`帐户。
{% endhint %}

_1\)_ 克隆具有ansible剧本的存储库和带有您要加入的网络名称的结帐分支（例如，mainnet的`core`和testnet的`sokol`

```text
git clone https://github.com/poanetwork/deployment-playbooks.git
cd deployment-playbooks
# for core mainnet
git checkout core
# OR for sokol testnet
git checkout sokol
# check that you ended up on a correct branch (look where the `*` is)
git branch
```

2\) 需要为ansible脚本创建两个带有ssh公钥的文件，以正确配置节点，并使用所需密钥的路径。

```text
cat ~/.ssh/id_poa-core.pub > files/admins.pub
cp files/admins.pub files/ssh_validator.pub
```

3\) 创建配置文件

```text
cat group_vars/all.network group_vars/validator.example > group_vars/all
```

4\) 编辑`group_vars/all`文件并注释掉与aws相对应的参数：

```text
#access_key
#secret_key
#awskeypair_name
#vpc_subnet_id
```

5\) 在`group_vars/all`中为以下参数设置由主持人提供给您的值：

* `NODE_FULLNAME` - 您的真实姓名（对网络的其他成员可见）
* `NODE_ADMIN_EMAIL` - 您的公共电子邮件地址（该网络的其他成员将可见）
* `MINING_KEYFILE` - 插入您的挖掘密钥库json文件的内容。 结果值应该用单引号引起来，并且看起来类似于：
* `MINING_KEYFILE: '{"address":"..."}'`
* `MINING_ADDRESS` - 插入您的挖矿密钥地址，例如
* `MINING_ADDRESS: "0x..."`
* `MINING_KEYPASS` - 插入您的采矿密钥密码

8\) 在`group_vars/all`中为以下参数设置由主持人提供给您的值：

* `NETSTATS_SERVER`
* `NETSTATS_SECRET`

9\) 在`group_vars/all`中设置以下选项：

```text
allow_validator_ssh: true
allow_validator_p2p: true
associate_validator_elastic_ip: false
```

{% hint style="warning" %}
仔细检查`allow_validator_ssh`为`true`，否则您将无法连接到该节点。
{% endhint %}

_10\)_ 使用服务器的IP地址创建`hosts`文件（例如192.0.2.1）：

```text
[validator]
192.0.2.1
```

11\) 运行Ansible Playbook，将--key-file路径替换为所需的SSH密钥

```text
ansible-playbook -i hosts site.yml -K --key-file "~/.ssh/id_poa-core"
```

12\) 在浏览器中打开`NETSTATS_SERVER` URL，并检查名为`NODE_FULLNAME`的节点是否出现在列表中

13\) [在验证器DApp中设置元数据](../../validator-dapps/validators-metadata-dapp.md)

### 仅**Sokol测试网**说明：

{% hint style="info" %}
如果要将节点部署到CORE网络，请跳过此步骤。 您不应该公开您的`enode`，因为它将使您的验证器节点成为拒绝服务攻击的简单目标。
{% endhint %}

如果要在测试网上（sokol）进行部署，请执行以下步骤：登录到节点并从Parity日志中获取enode：  


如果没有访问`root`的权限，则可以使用`sudo`用户，在连接到远程计算机后在命令前附加`sudo`

```text
ssh root@192.0.2.1
grep enode /home/validator/logs/parity.log
```

_复制`enode` uri并将其发送给仪式主持人。 如果找不到此行，请重新启动_Parity

```text
systemctl restart poa-parity
```

然后再试一次。 如果仍然找不到`enode`uri，请使用以下命令重新启动所有服务。

_注意_如果在Parity重新启动后您发现在`NETSTATS_SERVER` url上您的节点开始落后于其他节点（块号小于其他节点），请尝试重新启动统计信息服务（假设您以`root`身份连接）：

```text
su validator
pm2 restart all
```

之后刷新`NETSTATS_SERVER` URL并检查您节点的块号。 如果您的节点仍然不活动或缺少`enode`，请登录到`root`帐户并重新启动。 如果没有访问root的权限，则可以使用`sudo`用户，在连接到远程计算机后在命令前附加`sudo`

```text
su
shutdown -r now
```

