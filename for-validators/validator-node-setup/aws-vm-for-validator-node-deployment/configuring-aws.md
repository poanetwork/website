# 配置AWS

1. 注册（如果尚未注册）并登录到AWS管理控制台：[https://aws.amazon.com/console/](https://aws.amazon.com/console/) 
2. 创建cli的凭据，请打开IAM主页 [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home)，在左侧导航栏上选择用户“Users”，然后单击添加用户“Add user”。 选择一个用户名，然后在程序访问“Programmatic access”中检查访问类型“Access type”。 注意：为清楚起见，我们建议在Ansible Control Station和远程节点上使用相同的用户名。 例如，可以在Ansible控制站和远程便笺上创建一个名为“ ubuntu”的用户。 
3. 单击下一步：权限“Next: Permissions”-您可以选择任何可用选项，而直接附加现有策略“Attach existing policies directly”是最简单的选项。 在策略类型列表中，搜索然后选中“ AmazonEC2FullAccess”。 点击下一步：查看“Next:Review”。 查看您的帐户，然后单击创建用户“Create user”继续。 
4. **在不离开此页面的情况下复制访问密钥ID“**Access Key ID**”和**秘密访问密钥**“**Secret Access Key**”非常重要**，因为以后没有其他方法可以检索秘密访问密钥“Secret Access Key”，因此您将不得不重新启动并创建另一个用户。 复制此重要信息后，选择关闭“Close” 
5. 复制并保存AWS密钥后，下一步就是上传SSH公钥。 在页面的左上角，选择“Services -&gt; EC2”。 在左侧边栏中，选择Network & Security" -&gt; "Key Pairs"。 点击“导入密钥对”。 为该密钥对命名，否则将使用文件的基本名称（默认为`id_rsa`）。 浏览您的Ansible Control Station文件系统以获取公钥，或复制/粘贴：

   ```text
   pbcopy < ~/.ssh/id_rsa.pub
   ```

   T这会将您的公钥复制到剪贴板中，然后可以粘贴。  

6. 配置aws cli：

   ```text
   aws configure
   ```

   从以前提供您的凭据（访问密钥ID和秘密访问密钥）。 为您的帐户选择一个区域（例如us-east-2）并选择输出格式（建议使用json）。  

7. 检查密钥对是否正确导入：

   ```text
   aws ec2 describe-key-pairs
   ```

   您应该在列表中看到密钥对名称。

{% hint style="success" %}
继续阅读[下载和配置脚本](download-and-configure-playbook.md)
{% endhint %}

