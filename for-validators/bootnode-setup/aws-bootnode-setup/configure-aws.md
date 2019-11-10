# 配置AWS

1. 注册（如果尚未注册）并登录到AWS管理控制台：[https://aws.amazon.com/console/](https://aws.amazon.com/console/) 
2. 要创建cli的凭据，请打开IAM主页 [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home), 选择左侧mav栏上的 "Users" 然后点击 "Add user"。选择一个用户名，然后在 "Programmatic access" 中检查 "Access type"。然后点击 "Next:Permissions"。 
3. 您可以选择任何可用选项，但是 "Attach existing policies directly" 是最简单的选项。 在策略类型列表中搜索，然后检查 "AmazonEC2FullAccess"。点击 "Next:Review". 。 查看您的帐户，然后单击 "Create user" 继续。 
4. **在不离开此页面的情况下复制 "Access Key ID" 和 "Secret Access Key" 非常重要**，因为以后没有其他方法可以检索 "Secret Access Key" ，因此您将不得不重新启动并创建另一个用户。 复制此重要信息后，选择"Close"。 
5. 复制并保存AWS密钥后，下一步就是上传SSH公钥。 在页面的左上角，选择 "Services -&gt; EC2"。 在左侧边栏中，选择 "Network & Security" -&gt; "Key Pairs"。点击 "Import Key Pair"。 为该密钥对命名，否则将使用文件的基本名称（默认为`id_rsa`）。 浏览文件系统以获取公钥，或复制/粘贴：

   ```text
   # if you are on MacOS
   pbcopy < ~/.ssh/id_rsa.pub
   ```

   这会将您的公钥复制到剪贴板中，然后可以粘贴。  

6. 配置aws cli：

   ```text
   aws configure
   ```

   从以前提供您的凭据（Access Key ID and Secret Access Key）。 为您的帐户选择一个区域（例如`us-east-2`）并选择输出格式（建议使用`json`）。  

7. 检查密钥对是否正确导入：

   ```text
   aws ec2 describe-key-pairs
   ```

   您应该在列表中看到密钥对名称。

{% hint style="success" %}
继续[下载并配置脚本](download-and-configure-playbook.md)
{% endhint %}



