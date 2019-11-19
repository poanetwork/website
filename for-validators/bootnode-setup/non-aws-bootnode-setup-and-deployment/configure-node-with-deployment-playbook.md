# 使用部署手册配置节点

要运行脚本，您将需要服务器上具有`sudo`特权且可以通过SSH公钥登录的用户。 默认情况下，假定此用户称为`ubuntu`。 如果您已经有一个满足以下要求的不同名称的用户，请在`-hosts:all` 部分的`site.yml`顶部将行`user:ubuntu`更改为您拥有的`sudo`用户

```text
---
- hosts: all
  user: ubuntu
  become: True
...
```

{% hint style="info" %}
脚本还将另外创建一个名为`bootnode`的新非特权用户，并将您的ssh公钥添加到`root`帐户。
{% endhint %}

1\) 克隆具有ansible剧本的存储库和带有您要加入的网络名称的结帐分支（例如，mainnet的`core`和testnet的`sokol`

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
cp files/admins.pub files/ssh_bootnode.pub
```

3\) 创建配置文件

```text
cat group_vars/all.network group_vars/bootnode.example > group_vars/all
```

4\) 编辑`group_vars/all`文件并注释掉与aws相对应的参数：

```text
#access_key
#secret_key
#awskeypair_name
#vpc_subnet_id
```

5\) 在`group_vars/all`中为以下参数设置由主持人提供给您的值：

* `NODE_FULLNAME`
* `NODE_ADMIN_EMAIL`
* `NETSTATS_SERVER`
* `NETSTATS_SECRET`

6\)  如下设置以下选项：

```text
allow_bootnode_ssh: true
allow_bootnode_p2p: true
allow_bootnode_rpc: false
associate_bootnode_elastic_ip: false
```

{% hint style="warning" %}
仔细检查`allow_bootnode_ssh`为`true`，否则您将无法连接到该节点。
{% endhint %}

7\) 使用服务器的IP地址创建`hosts`主机（例如192.0.2.1）：

```text
[bootnode]
192.0.2.1
```

8\) 运行ansible脚本，将`--key-file` 路径替换为所需的SSH密钥

```text
ansible-playbook -i hosts site.yml -K --key-file "~/.ssh/id_poa-core"
```

9\) 在浏览器中打开`NETSTATS_SERVER` URL，并检查名为`NODE_FULLNAME`的节点是否出现在列表中

10\) 登录到该节点并从Parity日志中获取enode：  
如果没有访问`root`的权限，则可以使用`sudo`用户，在连接到远程计算机后在命令前附加`sudo`

```text
ssh root@192.0.2.1
grep enode /home/bootnode/logs/parity.log
```

复制`enode` uri并将其发送给仪式主持人。 如果找不到此行，请重新启动Parity

```text
systemctl restart poa-parity
```

然后再试一次。 如果仍然找不到`enode` uri，请使用以下命令重新启动所有服务。

{% hint style="info" %}
如果在奇偶校验重新启动后您发现在NETSTATS\_SERVER url上您的节点开始落后于其他节点（块号小于其他节点），请尝试重新启动统计信息服务（假设您以root身份连接）：
{% endhint %}

```text
su bootnode
pm2 restart all
```

之后刷新`NETSTATS_SERVER` URL并检查您节点的块号。 如果您的节点仍然不活动或缺少`enode`，请登录到root帐户并重新启动。  


{% hint style="info" %}
如果没有访问`root`的权限，则可以使用`sudo`用户，在连接到远程计算机后在命令前附加`sudo`
{% endhint %}

```text
su
shutdown -r now
```

