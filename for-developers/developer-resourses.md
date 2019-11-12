---
description: 一般信息和链接
---

# 开发人员资源

## 一般信息 <a id="general-information"></a>

| 区块大小 | 块生成速度 | Gas价格 | 补丁集 | 原生令牌 | 网络ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 10,000,000 Gas | 5 sec | 1 GWei | St.Petersburg | POA | 99 |

## 区块链浏览器 <a id="blockchain-explorer"></a>

BlockScout是POA网络的官方区块链浏览器

* POA Core核心网络: [https://blockscout.com/poa/core](https://blockscout.com/poa/core)
* Sokol测试网络: [https://blockscout.com/poa/sokol](https://blockscout.com/poa/sokol)

你可以通过BlockScout：

* 查看区块，交易，账户，余额，代币转移 
* 通过API访问区块链数据 
* 阅读和验证智能合约

## JSON RPC端点 <a id="json-rpc-endpoints"></a>

POA和Nodesmith提供了端点。 它们用于连接到网络。 当使用MetaMask或其他web3钱包连接到POA网络时，请使用这些端点连接DApp。

### POA RPC <a id="poa-rpc"></a>

| ​POA Core核心网络 | ​ |
| :--- | :--- |
| URL | ​[https://core.poa.network](https://core.poa.network) |
| Network ID | 99 |

| **POA Sokol 测试网络** |  |
| :--- | :--- |
| URL | https://sokol.poa.network |
| Network ID | 77 |

### **Nodesmith RPC** <a id="nodesmith-rpc"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x200B;POA Core &#x6838;&#x5FC3;&#x7F51;&#x7EDC;</th>
      <th style="text-align:left">&#x200B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">URL</td>
      <td style="text-align:left">
        <p>&#x200B;<a href="https://poa.api.nodesmith.io/v1/dai/jsonrpc?apiKey=YOUR_API_KEY">https://poa.api.nodesmith.io/v1/poa/jsonrpc?apiKey=</a>&#x200B;YOUR_API_KEY</p>
        <p>(requires <a href="https://nodesmith.io/docs/#/overview/httpsQuickstart">free Nodesmith account for your API key</a>):</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Network ID</td>
      <td style="text-align:left">99</td>
    </tr>
  </tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">POA Sokol &#x6D4B;&#x8BD5;&#x7F51;&#x7EDC;</th>
      <th style="text-align:left">&#x200B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">URL</td>
      <td style="text-align:left">
        <p><a href="https://poa.api.nodesmith.io/v1/sokol/jsonrpc?apiKey=YOUR_API_KEY">https://poa.api.nodesmith.io/v1/sokol/jsonrpc?apiKey=YOUR_API_KEY</a>
        </p>
        <p>(requires <a href="https://nodesmith.io/docs/#/overview/httpsQuickstart">free Nodesmith account for your API key</a>):</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Network ID</td>
      <td style="text-align:left">77</td>
    </tr>
  </tbody>
</table>## 桥接POA &lt;&gt; POA20 <a id="bridge-dai-less-than-greater-than-xdai"></a>

需要POA桥接器才能从POA核心网络和以太坊主网上的薄荷POA20移动锁定的POA令牌。

* TokenBridge UI网桥界面 [https://bridge.poa.net/](https://bridge.poa.net/)

## 水龙头 <a id="additional-resources"></a>

* Sokol测试网络水龙头: [https://faucet.poa.network](https://faucet.poa.network/) 获取免费的SPOA令牌以在Sokol测试网上进行测试 
* [ERC20测试令牌水龙头](erc20-test-token-faucet.md) 可以在_Sokol_或POA Core上使用。

## 额外资源 <a id="additional-resources"></a>

### **POA**

* WebSockets端点（可用于为POA设置BlockScout） [ws://54.144.107.14:8546](ws://54.144.107.14:8546)
* 存档Fullnode端点（用于为POA设置BlockScout） [http://54.144.107.14:8545](http://54.144.107.14:8545)
* 链规范文件和POA网络的已知引导节点 [https://github.com/poanetwork/poa-chain-spec/tree/core](https://github.com/poanetwork/poa-chain-spec/tree/core)
* Netstats，POA链节点概述 [https://core-netstat.poa.network](https://core-netstat.poa.network)
* 部署到POA的DApp：已部署DApp的部分列表以及统计信息和链接 [https://www.stateofthedapps.com/rankings/platform/poa](https://www.stateofthedapps.com/rankings/platform/poa)

### POA Sokol测试网络

* WebSockets端点（对于为Sokol设置BlockScout可能有用） [ws://3.85.253.242:8546](ws://3.85.253.242:8546)
* 存档Fullnode端点（对于为Sokol设置BlockScout可能有用） [http://3.85.253.242:8545](http://3.85.253.242:8545/)
* 链[规范](https://github.com/poanetwork/poa-chain-spec/blob/sokol/spec.json)文件和Sokol网络的已知[引导节点](https://github.com/poanetwork/poa-chain-spec/blob/sokol/bootnodes.txt)
* 以太坊网络统计（Netstats）以及Sokol网络上的节点列表。 节点应安装netstats代理才能在netstats中列出。 [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network/)
* 治理DApp： 要使用管理dapp，请在您的Nifty Wallet中切换到Sokol网络
  * 验证人DApp: [https://validators.poa.network/ ](https://validators.poa.network/) 在DApp中，任何人都可以获取有关Sokol网络验证器及其密钥的信息。
  * 投票DApp: [https://voting.poa.network/ ](https://voting.poa.network/) 在DApp中，任何人都可以在_Sokol_网络上获取有关治理决策的信息。

