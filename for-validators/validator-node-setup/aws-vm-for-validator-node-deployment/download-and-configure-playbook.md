# 下载并配置脚本

如果您尚未添加github信息，则可能需要添加。 这可能需要创建一个新的 "Personal Access Token".

1. 克隆具有ansible脚本的存储库和带有您要加入的网络名称的结帐分支（例如，mainnet的`core`和testnet的`sokol`）

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

  2. 使用SSH密钥准备文件

```text
cat ~/.ssh/id_rsa.pub > files/admins.pub
cp files/admins.pub files/ssh_validator.pub
```

   3. 使用配置设置创建文件：

```text
cat group_vars/all.network group_vars/validator.example > group_vars/all
```

    4. 选择子网，请运行以下命令

```text
aws ec2 describe-subnets
```

选择具有"State": "available" 和非零 "AvailableIpAddressCount" 的任何子网。 您需要复制/保存此子网的 "SubnetId" 以供以后使用。

   5. 打开 `group_vars/all` 并编辑以下配置选项：

```text
nano group_vars/all
```

进行以下编辑：

* `access_key` - 您的AWS "Access Key ID"
* `secret_key` - 您的AWS "Secret Access Key"
* `awskeypair_name` - 您在AWS上上传的ssh密钥对的名称（默认为`id_rsa`）
* `vpc_subnet_id` - 插入您选择的 "SubnetId" 。 下一行应如下所示：

  ```text
  vpc_subnet_id: "subnet-..."
  ```

* `NODE_FULLNAME` - 输入您的节点名称（网络的其他成员可以看到该名称）。 请向仪式主持人咨询有关引导节点的命名约定。
* `NODE_ADMIN_EMAIL` - 输入您的公开电子邮件（网络的其他成员可以看到）
* `NETSTATS_SERVER` - 这应该是礼仪大师提供给您的网址
* `NETSTATS_SECRET` - 这应该是礼仪大师提供给您的密码
* `MINING_KEYFILE`-插入挖矿密钥库文件的内容。 结果值应该用单引号引起来，并且看起来类似于：
* ```text
  MINING_KEYFILE: '{"address":"..."}'
  ```
* `MINING_ADDRESS` - 插入您的挖矿密钥地址，例如：

  ```text
  MINING_ADDRESS: "0x..."
  ```

* `MINING_KEYPASS` - 插入您的挖掘密钥的密码
* 请与礼节主持人仔细检查网络中当前的限制气体限制，并将其与`BLK_GAS_LIMIT`选项中的值进行比较。 当前默认设置为“BLK\_GAS\_LIMIT: "8000000”。
* `allow_validator_ssh` - 如果计划以后通过ssh访问节点，则将此值设置为`true`
* `allow_validator_p2p` - 将此值设置为`true`以使您的节点可被同级发现`associate_validator_elastic_ip` - 如果要为此节点配置AWS Elastic IP，请将其设置为`true`

   6. 检查`image` 和`region`属性中的值。如果您的AWS区域与区域中的一个`region` 不匹配，则需要将区域替换为正确的`region` ，然后从此列表中选择图像this list [https://cloud-images.ubuntu.com/locator/ec2/](https://cloud-images.ubuntu.com/locator/ec2/)

打开此页面，向下滚动，从第一个（"Zone"）下拉列表中选择您的区域，从第二个（“Name”）下拉列表中选择`xenial`，从第五个（“Instance type”）中选择`hvm:ebs-ssd`。 这应该将您限制为一个选项，从“ AMI-ID”列复制值并将其粘贴到`image`属性中。

  7. 您也可以为`validator_instance_type`选择其他值。 对于`region: "us-east-2"`，我们建议使用`m4.xlarge`。 通过以下网址确认您所在地区可用实例类型的选项：[https://aws.amazon.com/ec2/pricing/on-demand/](https://aws.amazon.com/ec2/pricing/on-demand/)

{% hint style="success" %}
继续阅读[部署](deployment.md)
{% endhint %}



