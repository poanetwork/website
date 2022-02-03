# Connect to Pocket Decentralized Network

{% hint style="warning" %}
**Nifty Wallet is discontinued.** \
As a result of changing crypto market conditions and to continually improve support for our growing family of Gnosis Chain products, certain existing products will be retired in 2022. This list includes the **Nifty Wallet browser wallet**. Nifty Wallet extension will be delisted from Google Chrome web store in the near future.&#x20;

[See instructions ](./#move-export-an-address)to move your address to another wallet.
{% endhint %}

Nifty allows users to easily connect to a decentralized network rather than strictly through Infura (as is the case for mainnet interaction with MetaMask). The [Pocket Network](https://www.pokt.network) provides access and routes data to full service, decentralized blockchain nodes.

1\) Open Nifty Wallet, connect to your desired network, and select **Settings** from the three-line menu.

![](../../.gitbook/assets/settings\_1.png)

2\) Scroll down to the Provider section:

1. Select Switch to Decentralized Provider (Pocket)
2. Press the back arrow to return to your wallet.

![](../../.gitbook/assets/settings\_2.png)

3\) Thats it! Now you can send a transaction as you normally would, and it will be processed with the Pocket Network. Transactions times may increase slightly. Note that not all chains are supported by Pocket: Supported chains include ([see here for a full list](https://docs.pokt.network/docs/supported-networks)):

| Network / Client                                          | NetID |
| --------------------------------------------------------- | ----- |
| Ethereum **Mainnet** network (PoW//cross-client)          | 1     |
| Ethereum **Ropsten** testnet (PoW//cross-client)          | 3     |
| Ethereum **Rinkeby** testnet (POA - Clique//Geth)         | 4     |
| Ethereum **Goerli** testnet (POA-Clique//cross-client)    | 5     |
| Ethereum **Kovan** testnet (POA-AURA//parity, nethermind) | 42    |
| **POA** Core network (POA-AURA//parity, nethermind)       | 99    |
| **POA** Sokol testnet (POA-AURA//parity, nethermind)      | 77    |
| **xDai** network (POA-AURA//parity, nethermind)           | 100   |
