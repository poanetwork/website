---
description: 1inch令牌交换聚合器显示可用汇率，并且可以将交换拆分为多笔交易
---

# 在1inch.exchange上交换POA20令牌

1inch.exchange提供了将POA20与大量其他ERC20令牌交换的功能。 该交易所汇总了[几个不同的去中心化交易所](../about-poa-token/poa-and-poa20-exchanges.md)的汇率，并提供了最佳汇率。 功能包括专用的DApp（不是必要的）和[GasToken](https://gastoken.io/)利用率，从而降低了交易成本。

首先，启用web3钱包扩展程序，例如[Nifty Wallet](../wallets/nifty-wallet/)（在本教程中使用）或MetaMask。 该帐户必须包含少量以太币才能进行交易。

## 将ETH交换为POA20

{% hint style="info" %}
只要通过一种受支持的交易所（如Bancor或Uniswap）涵盖了任何令牌组合，就可以将其用于交换。
{% endhint %}

1\) 转至 [1inch.exchange](https://1inch.exchange)

1. 选择被转换的**From**令牌 - 在这种情况下，我们选择了ETH。
2. 输入你被转换的以太坊的数量**Amount** \(.01\).
3. 选择要转换的**To**令牌. 我们要将以太坊转换为POA20
4. 我们可以看到该金额将根据最佳汇率（115.582 ...）已自动填充。

![](../../.gitbook/assets/1inch1.png)

2\) 查看下面的价格。 在此示例中，Bancor提供了最佳汇率，但是Bancor和Uniswap之间的利润很小。 我们正在交换少量金额，因此有必要查看gas费用以确定最佳的整体价值。

![Bancor&#x5229;&#x7387;&#x7565;&#x9AD8;&#xFF0C;&#x4F46;&#x5C06;&#x9700;&#x8981;&#x66F4;&#x9AD8;&#xFF08;&#x4E0D;&#x53EF;&#x66F4;&#x6539;&#xFF09;&#x7684;&#x4EA4;&#x6613;&#x6210;&#x672C;](../../.gitbook/assets/rates.png)

3\) 要继续建议的交换（Bancor），请单击立即交换按钮**SWAP NOW**。 您的web3钱包应弹出以确认交易。 点击提交**Submit**以进行处理。

{% hint style="warning" %}
使用Bancor时，请勿更改gas价格（该价格已包含在合约对话中）。 更改价格将导致您的交易失败。
{% endhint %}

![Nifty Wallet&#x4EA4;&#x6613;&#x5F39;&#x51FA;&#x7A97;&#x53E3;&#x3002; &#x70B9;&#x51FB;&#x63D0;&#x4EA4;&#x4EE5;&#x8FDB;&#x884C;&#x5904;&#x7406;](../../.gitbook/assets/nifty1%20%282%29.png)

4\) 交易完成后，您将在Etherscan中看到一个检查交易的链接。 在这种情况下，gas费用大大低于18 GWEI，但仍占总成本的％。

![](../../.gitbook/assets/trans_fee.png)

5\) 为了进行比较，我们运行了相同的事务，但是这次选择了Uniswap。 要启用，我们关闭了Bancor DEX。 将交易100％移至Uniswap。

![&#x53D6;&#x6D88;&#x9009;&#x62E9;Bancor&#x9009;&#x9879;](../../.gitbook/assets/no_bancor.png)

6\) 在Nifty Wallet中，我们将建议的gas价格从11 GWEI更改为2 GWEI。

![&#x6211;&#x4EEC;&#x5C06;&#x6C7D;&#x6CB9;&#x4EF7;&#x683C;&#x964D;&#x81F3;2 GWEI](../../.gitbook/assets/nifty_2.png)

7\) Uniswap的最终交易费用成本为0.000154138以太（0.03美元），而Bancor的最终交易费用成本为0.004739292以太（0.87美元）。 即使Uniswap的费率稍差一些，但在这种情况下，包括费用在内的总成本还是有利的。

![Uniswap&#x4EA4;&#x6613;&#x7684;Etherscan&#x4EA4;&#x6613;&#x660E;&#x7EC6;](../../.gitbook/assets/etherscan2%20%282%29.png)

## 将POA20交换为BAT

该过程类似于将POA20转换为ETH，DAI或任何其他受支持的ERC20。 但是，它需要2个单独的交易，一个交易要解锁POA20，第二个交易要交换令牌。

在这种情况下，我们希望一些BAT可以帮助支持[Brave Browser](https://brave.com/)内容提供商。

 1\) 转至[1inch.exchange](https://1inch.exchange)

1. 选择被转换的**From**令牌 - 在这种情况下，我们选择了POA20。
2. 选择你要转换的POA20数量**Amount**。
3. 选择要转换的**To**令牌。我们想将POA20交换为BAT。.
4. 该金额将根据最佳汇率自动填充。
5. 点击解锁**Unlock**。

![&#x70B9;&#x51FB;&#x89E3;&#x9501;100&#x679A;POA20&#x4EE4;&#x724C;](../../.gitbook/assets/bat1%20%281%29.png)

2\) 在您的web3钱包中，检查交易费用。 您可以降低此交易的最高费用金额。 请点击提交**Submit。**

![&#x66F4;&#x4F4E;&#x7684;GWEI&#x4EE5;&#x8FDB;&#x884C;&#x89E3;&#x9501;&#x4EA4;](../../.gitbook/assets/niftybat1.png)

3\) 处理完第一笔交易后，将出现立即交换“**SWAP NOW**”按钮。 单击按钮并确认第二笔交易（**如果使用Bancor，请不要更改此交易的gas价格，否则您可以调整**）

4\) 您发送的交易将在界面中确认。

{% hint style="info" %}
在此期间，事务可能仍在处理中，单击以查看etherscan中的发送以获取详细信息。
{% endhint %}

![&#x4EA4;&#x6613;&#x6210;&#x529F;&#x53D1;&#x9001;](../../.gitbook/assets/battransconfirm.png)

5\) 检查您的Nifty Wallet余额。 如果您需要添加代币，请进行以下交易：

     1\) 选择“令牌”选项卡，然后单击**Add Token.**

![Click Add Token](../../.gitbook/assets/bat_add_token.png)

   2\) 搜索您的令牌，然后单击下一步“**Next**”添加。 确认添加。 _如果您的令牌没有出现，则可以在“自定义搜索”中输入令牌地址。_ 

![&#x70B9;&#x51FB;Next&#x6DFB;&#x52A0;](../../.gitbook/assets/bat-token-search.png)

   __3\) 点击添加令牌**Add Tokens**并确认。 

![Add Tokens to confirm](../../.gitbook/assets/confirm-add.png)

   4\) 您的令牌/余额将出现在列表中

![&#x663E;&#x793A;&#x5728;&#x94B1;&#x5305;&#x4E2D;&#x7684;BAT&#x6570;&#x91CF;](../../.gitbook/assets/bat-in-wallet.png)

6\) Etherscan浏览器显示交易记录。

![Etherscan&#x4E2D;&#x6240;&#x663E;&#x793A;&#x7684;POA20&#x5230;BAT&#x4EA4;&#x6362;&#x8BB0;&#x5F55;](../../.gitbook/assets/etherscan_bat.png)



