---
description: General information and links
---

# Developer Resources

## General Information <a id="general-information"></a>

### POA Core

| Block Size | Block Speed | Gas price | Patchset | Native token | Network ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ~10,000,000 Gas | 5 sec | 1 -10 GWei | Istanbul | POA | 99 |

{% hint style="info" %}
To mitigate an ongoing denial-of-service attack, validators decided to increase the gas price to a range between 1-10 Gwei. Each validator can determine their own value within this range.
{% endhint %}

### POA Sokol

| Block Size | Block Speed | Gas price | Patchset | Native token | Network ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ~10,000,000 Gas | 5 sec | 1 GWei | Istanbul | SPOA | 77 |

## Blockchain Explorers <a id="blockchain-explorer"></a>

1\) **BlockScout** is the official blockchain explorer for the POA Network. With this full-featured, open-source explorer you can view transactions, accounts & balances, access data via the API and read and verify smart contracts.

* POA Core Network: [https://blockscout.com/poa/core](https://blockscout.com/poa/core)
* Sokol Testnet: [https://blockscout.com/poa/sokol](https://blockscout.com/poa/sokol)

2\) **AnyBlock Analytics Explorer** is convenient for exploring recent transactions and blocks and locating basic information extremely quickly**.**

* Poa Core Network: [https://explorer.anyblock.tools/ethereum/poa/core/](https://explorer.anyblock.tools/ethereum/poa/core/)
* Sokol Testnet: [https://explorer.anyblock.tools/ethereum/poa/sokol/](https://explorer.anyblock.tools/ethereum/poa/sokol/)

## JSON RPC endpoints <a id="json-rpc-endpoints"></a>

There are endpoints provided by POA. They are used to connect to the network. Use these endpoints to connect with DApps or when connecting to the POA Network with MetaMask or other web3 wallets.

### POA RPC <a id="poa-rpc"></a>

| ​POA Core Network | ​ |
| :--- | :--- |
| URL | ​[https://core.poa.network](https://core.poa.network) |
| Network ID | 99 |

| **POA Sokol Testnet** |  |
| :--- | :--- |
| URL | [https://sokol.poa.network](https://sokol.poa.network) |
| Network ID | 77 |

### **Nodesmith RPC \(discontinued\)** <a id="nodesmith-rpc"></a>

{% hint style="warning" %}
Nodesmith RPC will be shut down by the end of December 2019.
{% endhint %}

| ​POA Core Network | ​ |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">URL</th>
      <th style="text-align:left">
        <p>&#x200B;<a href="https://poa.api.nodesmith.io/v1/dai/jsonrpc?apiKey=YOUR_API_KEY">https://poa.api.nodesmith.io/v1/poa/jsonrpc?apiKey=</a>&#x200B;YOUR_API_KEY</p>
        <p>(requires <a href="https://nodesmith.io/docs/#/overview/httpsQuickstart">free Nodesmith account for your API key</a>):</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">URL</th>
      <th style="text-align:left">
        <p><a href="https://poa.api.nodesmith.io/v1/sokol/jsonrpc?apiKey=YOUR_API_KEY">https://poa.api.nodesmith.io/v1/sokol/jsonrpc?apiKey=YOUR_API_KEY</a>
        </p>
        <p>(requires <a href="https://nodesmith.io/docs/#/overview/httpsQuickstart">free Nodesmith account for your API key</a>):</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>## TokenBridge UI

TokenBridge UI at [https://bridge.poa.net/](https://bridge.poa.net/)

## **Faucets** <a id="additional-resources"></a>

* Sokol Testnet Faucet: [https://faucet.poa.network](https://faucet.poa.network/) Get free SPOA tokens for testing on the _Sokol_ testnet 
* [ERC20 Test Token Faucet](getting-tokens-for-tests/erc20-test-token-faucet.md) Can be used on Sokol or POA Core. 

## DApp Management & Developer Tools

* [Terminal ](https://terminal.co)provides management, monitoring and analytics tools for DApp developers. 
* [Pocket](https://www.pokt.network/) provides a decentralized API layer for DApp developers \(IOS, Android & Web SDKs available\) and blockchain users.

## **Additional Resources** <a id="additional-resources"></a>

### **POA Mainnet**

* Chain spec files and known bootnodes of the POA network [https://github.com/poanetwork/poa-chain-spec/tree/core](https://github.com/poanetwork/poa-chain-spec/tree/core)
* Netstats, an overview of POA Chain nodes [https://core-netstat.poa.network](https://core-netstat.poa.network)
* DApps Deployed to POA: Partial list of deployed DApps along with statistics and links [https://www.stateofthedapps.com/rankings/platform/poa](https://www.stateofthedapps.com/rankings/platform/poa)

### POA Sokol Testnet

* Chain [spec](https://github.com/poanetwork/poa-chain-spec/blob/sokol/spec.json) files and known [bootnodes ](https://github.com/poanetwork/poa-chain-spec/blob/sokol/bootnodes.txt)of the _Sokol_ network
* [Ethereum Networks Stats ](https://github.com/cubedro/eth-netstats)\(Netstats\) with a list of nodes on Sokol network. Nodes should have netstats agent installed to be listed in the netstats. [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network/)
* Governance DApps: To use governance dapps please switch to Sokol network in your Nifty Wallet
  * Validators DApp: [https://validators.poa.network/ ](https://validators.poa.network/) In the DApp anyone can get information about validators of the _Sokol_ network and their keys
  * Voting DApp: [https://voting.poa.network/ ](https://voting.poa.network/) In the DApp anyone can get information about governance decisions on the _Sokol_ network.

