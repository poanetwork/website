# MoC：仪式密钥交换和生成大师

{% hint style="info" %}
如果您要加入当前的POA或Sokol网络，则可以继续进行“[当前验证者在新验证者中投票](current-validators-vote-in-new-validators.md)”。 这些说明用于网络启动。
{% endhint %}

1. 启动Chrome浏览器
2. 通过选择MetaMask上的`Network`下拉菜单，连接到MetaMask中所需的网络，并使用以下端点添加`Custom RPC`。
   * Core核心网络: `https://core.poa.network`
   * Sokol测试网络: `https://sokol.poa.network`
3. 使用提供的密码将初始密钥上传到MoC为您提供的MetaMask。
4. 将您的Chrome浏览器导航到[https://ceremony.poa.network/](https://ceremony.poa.network/)
5. 确保在MetaMask中选择了由MoC提供的`Initial Key`初始密钥。
6. 点击生成密钥"Generate keys"确认交易

{% hint style="danger" %}
**注意**：下一部分**非常**重要，必须正确完成，以便能够立即参与共识，在关闭浏览器窗口**之前**，请遵循以下指示。 打开记事本并复制所需的信息，如下所示。
{% endhint %}

1. 单击每个地址`Address`旁边的复制`Copy`按钮。 采矿，支出，投票。 将它们分别粘贴在记事本中。 
2. 单击每个密码`Password`旁边的复制`Copy`按钮，以匹配记事本中的结果地址。 采矿，支出，投票。 
3. 最后，单击“按钮”以下载每个密钥的JSON密钥库文件，并将记事本文件和所有3个密钥+初始密钥保存在安全的地方。

{% hint style="info" %}
存储密钥文件和信息的首选方法是存储在加密的驱动器上。例如 USB驱动器 

请不要忘记用于加密的密码，因为如果验证者的节点发生任何问题，您将丢失数据，并且必须淘汰旧密钥，而必须投出新密钥。
{% endhint %}

{% hint style="success" %}
Continue to [Prerequisites](validator-node-setup-prerequisites.md)
{% endhint %}



