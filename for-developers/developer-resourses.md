---
description: General information and links
---

# Developer Resources

## General Information <a id="general-information"></a>

| Block Size | Block Speed | Gas price | Patchset | Native token | Network ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 10,000,000 Gas | 5 sec | 1 GWei | St.Petersburg | POA | 99 |

## Blockchain Explorer <a id="blockchain-explorer"></a>

BlockScout is the official blockchain explorer for the POA [https://blockscout.com/poa/core](https://blockscout.com/poa/core)

With BlockScout you can

* view blocks, transactions, accounts, balances, token transfers
* access blockchain data via API
* read and verify smart contracts

## JSON RPC endpoints <a id="json-rpc-endpoints"></a>

There are endpoints provided by POA and Nodesmith. They are used to connect to the network.

### POA RPC <a id="poa-rpc"></a>

| ​ | ​ |
| :--- | :--- |
| URL | ​[https://core.poa.network](https://core.poa.network) |
| Network ID | 99 |

### **Nodesmith RPC** <a id="nodesmith-rpc"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x200B;</th>
      <th style="text-align:left">&#x200B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>URL</b>
      </td>
      <td style="text-align:left">
        <p>&#x200B;<a href="https://poa.api.nodesmith.io/v1/dai/jsonrpc?apiKey=YOUR_API_KEY">https://poa.api.nodesmith.io/v1/poa/jsonrpc?apiKey=</a>&#x200B;</p>
        <p>(requires <a href="https://nodesmith.io/docs/#/overview/httpsQuickstart">free Nodesmith account for your API key</a>):</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Network ID</td>
      <td style="text-align:left">99</td>
    </tr>
  </tbody>
</table>## Bridge POA &lt;&gt; POA20 <a id="bridge-dai-less-than-greater-than-xdai"></a>

The POA bridge is required to move locked POA token from POA Core network and mint POA20 on Ethereum 

You can access the bridge via:

* TokenBridge UI at [https://bridge.poa.net/](https://bridge.poa.net/)
* Interactions with smart contracts 

## **Additional resources** <a id="additional-resources"></a>

* WebSockets Endpoint \(can be useful to setup BlockScout for POA\) [ws://54.144.107.14:8546](ws://54.144.107.14:8546)
* Archive Fullnode Endpoint \(Useful for setting up BlockScout for POA\) [http://54.144.107.14:8545](http://54.144.107.14:8545)
* Alternative POA explorer based on [Etherchain Light](https://github.com/gobitfly/etherchain-light): [https://core-explorer.poa.network](https://core-explorer.poa.network)
* Chain spec files and known bootnodes of the POA network [https://github.com/poanetwork/poa-chain-spec/tree/core](https://github.com/poanetwork/poa-chain-spec/tree/core)
* Netstats, an overview of POA Chain nodes [https://core-netstat.poa.network](https://core-netstat.poa.network)
* DApps Deployed to POA: Partial list of deployed DApps along with statistics and links [https://www.stateofthedapps.com/rankings/platform/poa](https://www.stateofthedapps.com/rankings/platform/poa)

