---
description: General information and links
---

# Developer Resources

## General Information <a id="general-information"></a>

| Block Size | Block Speed | Gas price | Patchset | Native token | Network ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 10,000,000 Gas | 5 sec | 1 GWei | St.Petersburg | POA | 99 |

## Blockchain Explorer <a id="blockchain-explorer"></a>

BlockScout is the official blockchain explorer for the POA Network

* POA Core Network: [https://blockscout.com/poa/core](https://blockscout.com/poa/core)
* Sokol Testnet: [https://blockscout.com/poa/sokol](https://blockscout.com/poa/sokol)

With BlockScout you can

* View blocks, transactions, accounts, balances, token transfers
* Access blockchain data via API
* Read and verify smart contracts

## JSON RPC endpoints <a id="json-rpc-endpoints"></a>

There are endpoints provided by POA and Nodesmith. They are used to connect to the network. Use these endpoints to connect with DApps or when connecting to the POA Network with MetaMask or other web3 wallets.

### POA RPC <a id="poa-rpc"></a>

| ​POA Core Network | ​ |
| :--- | :--- |
| URL | ​[https://core.poa.network](https://core.poa.network) |
| Network ID | 99 |

| **POA Sokol Testnet** |  |
| :--- | :--- |
| URL | https://sokol.poa.network |
| Network ID | 77 |

### **Nodesmith RPC** <a id="nodesmith-rpc"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x200B;POA Core Network</th>
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
      <th style="text-align:left">POA Sokol Testnet</th>
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
</table>## Bridge POA &lt;&gt; POA20 <a id="bridge-dai-less-than-greater-than-xdai"></a>

The POA bridge is required to move locked POA tokens from the POA Core network and mint POA20 on the Ethereum Mainnet.

* TokenBridge UI at [https://bridge.poa.net/](https://bridge.poa.net/)

## **Faucets** <a id="additional-resources"></a>

* Sokol Testnet Faucet: [https://faucet.poa.network](https://faucet.poa.network/) Get free SPOA tokens for testing on the _Sokol_ testnet 
* [ERC20 Test Token Faucet](erc20-test-token-faucet.md) Can be used on Sokol or POA Core. 

## DApp Management & Developer Tools

* [Terminal ](https://terminal.co)provides management, monitoring and analytics tools for DApp developers. 
* [Pocket](https://www.pokt.network/) provides a decentralized API layer for DApp developers \(IOS, Android & Web SDKs available\) and blockchain users.

## **Additional Resources** <a id="additional-resources"></a>

### **POA Mainnet**

* WebSockets Endpoint \(can be useful to setup BlockScout for POA\) [ws://54.144.107.14:8546](ws://54.144.107.14:8546)
* Archive Fullnode Endpoint \(Useful for setting up BlockScout for POA\) [http://54.144.107.14:8545](http://54.144.107.14:8545)
* Chain spec files and known bootnodes of the POA network [https://github.com/poanetwork/poa-chain-spec/tree/core](https://github.com/poanetwork/poa-chain-spec/tree/core)
* Netstats, an overview of POA Chain nodes [https://core-netstat.poa.network](https://core-netstat.poa.network)
* DApps Deployed to POA: Partial list of deployed DApps along with statistics and links [https://www.stateofthedapps.com/rankings/platform/poa](https://www.stateofthedapps.com/rankings/platform/poa)

### POA Sokol Testnet

* WebSockets Endpoint \(can be useful to setup BlockScout for Sokol\) [ws://3.85.253.242:8546](ws://3.85.253.242:8546)
* Archive Fullnode Endpoint \(can be useful to setup BlockScout for Sokol\) [http://3.85.253.242:8545](http://3.85.253.242:8545/)
* Chain [spec](https://github.com/poanetwork/poa-chain-spec/blob/sokol/spec.json) files and known [bootnodes ](https://github.com/poanetwork/poa-chain-spec/blob/sokol/bootnodes.txt)of the _Sokol_ network
* [Ethereum Networks Stats ](https://github.com/cubedro/eth-netstats)\(Netstats\) with a list of nodes on Sokol network. Nodes should have netstats agent installed to be listed in the netstats. [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network/)
* Governance DApps: To use governance dapps please switch to Sokol network in your Nifty Wallet
  * Validators DApp: [https://validators.poa.network/ ](https://validators.poa.network/) In the DApp anyone can get information about validators of the _Sokol_ network and their keys
  * Voting DApp: [https://voting.poa.network/ ](https://voting.poa.network/) In the DApp anyone can get information about governance decisions on the _Sokol_ network.

