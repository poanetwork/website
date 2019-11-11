# 部署方式

## 创建实例

1\) 在配置了所有选项之后，您首先需要创建一个实例：（您仍应位于：~/deployment-playbooks）

```text
ansible-playbook validator.yml
```

运行此脚本将创建并启动远程AWS实例。 除非您未设置密码短语或您最近输入密码，否则该脚本还会询问您SSH密钥密码短语。

2\) 完成此过程后，检查脚本的输出并记下IP（例如`192.0.2.1`）地址和AWS InstanceID（例如`i-0123456789abcdef0`）以备后用。 如果选择使用弹性IP，请记下节点的最终IP地址。

## 配置实例

1\) 创建具有以下内容的`hosts`文件（假定IP地址为`192.0.2.1`，从上一步中收集）

```text
touch hosts
echo [validator] > hosts
echo 192.0.2.1 >> hosts

NOTE:  Feel free to edit the hosts file directly with any text editor (vi, pico, etc.) - file must contain at minimum:
[validator]
192.0.2.1
```

2\) 运行以下脚本来配置您的远程节点实例：

```text
ansible-playbook -i hosts site.yml
```

如果您收到无法通过SSH访问主机的错误，请稍等片刻，然后重新启动。 可能会出现此错误，因为创建后重新启动了AWS实例，这可能需要一些时间才能完成。

3\) 打开`NETSTAT_SERVER`的URL并检查您的节点是否已出现在列表中

## 在DApp中设置元数据

遵循有关如何更新[验证人元数据的指南](../../validator-dapps/validators-metadata-dapp.md)。

## 获取礼仪大师的enode uri

{% hint style="warning" %}
**注意**如果要将节点部署到CORE网络，请跳过此步骤。 您不应公开自己的`enode`，因为它将使您的验证器节点成为拒绝服务攻击的简单目标
{% endhint %}

如果要在测试网上（sokol）进行部署，请按照以下步骤操作： 

1\) 登录到该节点并从奇偶校验日志中获取enode：

```text
ssh root@192.0.2.1 OR, if root SSH access is not enabled:
ssh -l ubuntu 192.0.2.1  #NOTE: replace 'ubuntu' with a different remote node user if you are not using the recommended example user.  Once logged in, become Super User by executing:

sudo su    #NOTE:  enter the 'ubuntu' user password, or other user password if you have created a different user.  You should now be Super User, with all of the powers and identity of the 'root' user.  Be careful!

grep enode /home/validator/logs/parity.log
```

2\) 复制`enode` uri并将其发送给仪式主持人。 如果找不到此行，请重新启动奇偶校验

```text
systemctl restart poa-parity
```

然后再试一次。 如果仍然找不到`enode` uri，请使用以下命令重新启动所有服务。

{% hint style="info" %}
如果奇偶校验重新启动后，您发现`NETSTATS_SERVER` url上您的节点开始落后于其他节点（块号小于其他节点）并且几分钟后仍未赶上，_请尝试以下操作：_ 
{% endhint %}

1\) 尝试重新启动统计信息服务（假设您以`root`用户身份连接）：

```text
su validator
pm2 restart all
```

之后，在浏览器中刷新`NETSTATS_SERVER` URL，然后再次检查节点的块号。 如果您的节点仍然不活动或缺少`enode`条目

2\) 登录到root帐户并重新启动操作系统。

重新启动远程服务器之前，**请等待**至少五分钟，以使节点“赶上”，这只能作为最后的手段。

```text
su
shutdown -hr now
```

## 配置对节点的访问

稍后，您可能希望更改节点的访问选项。 例如，最初您可能已经禁用了通过ssh的访问，但现在想重新启用它。 这些选项由文件group\_vars / all中的参数设置：

* `allow_validator_ssh` - `true`/`false` - 通过ssh允许/拒绝访问
* `allow_validator_p2p` - `true`/`false` - 允许/拒绝对等发现

进行更改后，请重新运行脚本：

```text
ansible-playbook -i hosts site.yml
```

{% hint style="info" %}
该脚本同时适用于具有名为`validator-security`的安全组的所有实例，以及技术上在“主机”文件中的所有其他服务器。 仅当您运行多个验证程序节点或其他实例时，此注释才有意义。.
{% endhint %}

## 删除实例

**如果要删除您的AWS实例：**

a. 通过AWS GUI进行操作：打开AWS管理控制台[https://console.aws.amazon.com/ec2/v2/home\#Instances](https://console.aws.amazon.com/ec2/v2/home#Instances)检查要删除的实例，单击Actions&gt; Instance State&gt; Terminate。

b. 通过aws cli执行此操作：获取AWS实例ID（您之前保存的ID，或者您可以在AWS管理控制台中查找它）并运行

```text
aws ec2 terminate-instances --instance-ids i-0123456789abcdef0
```

（将`i-0123456789abcdef0`替换为您的实际AWS InstanceID）。

{% hint style="danger" %}
此操作是不可逆的！ 如果要重新部署，则必须从头开始创建一个新实例。
{% endhint %}

