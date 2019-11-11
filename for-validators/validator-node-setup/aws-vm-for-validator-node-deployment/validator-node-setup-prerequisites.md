# 验证程序节点设置先决条件

**0.选择您的本地Ansible Control Station用户名。**

* 为了清楚起见，您可能希望在Ansible Control Station和远程节点上使用相同的用户名。 例如，可以在Ansible控制站和远程便笺上创建一个名为“ ubuntu”的用户。 如果可以的话，为Ansible Control Station使用专用节点可以在不使用时关闭电源或将其移出网络是理想的选择。 如果使用本地工作站，则创建和使用Ansible Control Station专用用户可减少发生错误的可能性。 当您创建新的本地用户时（建议使用示例“ ubuntu”用户名），请确保该用户在Ansible Control Station上具有sudo或su（超级用户）权限。 本示例的其余部分假定您的用户位于sudo组中。

#### 1. git

1. 检查您是否已安装git

   ```text
   git --version
   ```

   如果不是，请按照[此处](https://www.python.org/downloads/)的说明进行安装

#### 2. python & pip

1. 检查您是否已安装python 2版本&gt; = 2.6.5或python 3版本&gt; = 3.3

   ```text
   python --version
   ```

   如果不是，请从[此处](https://www.python.org/downloads/)选择合适的二进制文件进行安装  

2. 检查您是否安装了`pip` python软件包管理器

   ```text
   pip --version
   ```

   如果不是，请按照此处的说明进行安装。 基本上，您需要下载此脚本并将其保存在计算机上 [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py) 然后运行

   ```text
   python get-pip.py
   ```

#### 3. ansible

1. 请按照[本指南](http://docs.ansible.com/ansible/latest/intro_installation.html)进行安装。 例如，您可以使用pip来做到这一点：

   ```text
   sudo pip install ansible
   ```

2. 使用`pip`安装以下软件包：

   ```text
   sudo pip install boto
   sudo pip install boto3
   ```

#### 4. SSH keys

1. 检查您是否已经有密钥对：

   ```text
   ls -la ~/.ssh
   ```

   如果出现目录不存在或目录为空的错误，则需要按照以下说明进行操作。 如果您已经有密钥对，则可以跳过此部分。

2. 生成SSH密钥对

   ```text
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

   在其中插入您的电子邮件地址和一个强密码。 默认情况下，密钥将保存到`~/.ssh/`，并命名为`id_rsa`，而公共密钥为`~/.ssh/id_rsa.pub`。

#### 5. aws cli

1. 检查您是否安装了AWS CLI

   ```text
   aws --version
   ```

   如果不是，请按照以下说明进行安装。 最简单的方法是使用`pip`：

   ```text
   pip install awscli --upgrade --user
   ```

   安装了自制软件的Mac系统：

   ```text
   brew install awscli
   ```

{% hint style="success" %}
Continue to [Configuring AWS](configuring-aws.md)
{% endhint %}

