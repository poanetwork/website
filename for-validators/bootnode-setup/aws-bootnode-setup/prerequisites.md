# 先决条件

* git
* python & pip: 
  * python 2 version &gt;= 2.6.5 or python 3 version &gt;= 3.3 
* ansible
* SSH keys
* aws cli

## 1. git

1. 检查您是否已安装git

   ```text
   git --version
   ```

   如果没有，请按照[此处](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)的说明进行安装

## 2. python & pip

1. 检查您是否已安装python 2版本&gt; = 2.6.5或python 3版本&gt; = 3.3

   ```text
   python --version
   ```

   如果没有，请从[此处](https://www.python.org/downloads/)选择合适的二进制文件进行安装  

2. 检查您是否安装了`pip`python软件包管理器

   ```text
   pip --version
   ```

   如果没有，请按照[此处](https://pip.pypa.io/en/stable/installing/)的说明进行安装。 基本上，您需要下载此脚本并将其保存在计算机上[https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py)，然后运行

   ```text
   python get-pip.py
   ```

## 3. ansible

1. 请按照[本指南](http://docs.ansible.com/ansible/latest/intro_installation.html)进行安装。 例如，您可以使用`pip`来做到这一点：

   ```text
   sudo pip install ansible
   ```

2. 使用`pip`安装以下软件包：

   ```text
   sudo pip install boto
   sudo pip install boto3
   ```

## 4. SSH keys

1. 检查您是否已经有密钥对：

```text
ls -la ~/.ssh
```

{% hint style="info" %}
如果您已经有密钥对，则可以跳过此部分。
{% endhint %}

**2.** 生成SSH密钥对

```text
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

在其中插入您的电子邮件地址和一个强密码。 默认情况下，密钥将保存到`~/.ssh/`，并命名为`id_rsa`，而公共密钥为`~/.ssh/id_rsa.pub`。

## 5. aws cli

1. 检查您是否安装了AWS CLI

   ```text
   aws --version
   ```

   如果没有，请按照[以下说明](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)进行安装。 最简单的方法是使用`pip`：

   ```text
   pip install awscli --upgrade --user
   ```

   安装了自制软件的Mac系统：

   ```text
   brew install awscli
   ```

{% hint style="success" %}
继续[配置AWS](configure-aws.md)
{% endhint %}

