---
description: Low per-transaction fees enable applications to pay for user interactions
---

# Subsidized Transactions

### Subsidized Use Case: Kauri Article Registry

Kauri is a decentralized article repository, similar to Medium for web3. Users create articles, tutorials and documentation and publish them on the platform. 

When a user creates an article with Kauri, it is stored in [IPFS](https://ipfs.io/). Metadata like the author's name, article id, and IPFS hash is then committed on-chain to register ownership and creation time.

In a standard scenario, the user needs to create a transaction to publish the article, and another transaction for each and every update. This can become costly, unintuitive, and cumbersome for the article creator.

Ideally, a user should not have to pay for each transaction when publishing content, or worry about how much a transaction will cost. To address this problem, on-chain transaction payments can be shifted to a meta-transaction model, where a relayer is setup to pay all transaction costs.  Users don't need any Ether, they can simply provide their data and the deployed contracts and relayer take care of the rest.

However, this can be unsustainable on the Ethereum mainnet where gas costs fluctuate and may become expensive. If an application wants to scale, costs can rise very quickly.

By moving publication registration to the POA Network, Kauri is able to subsidize transaction costs by using meta-transactions. A full block on POA costs less than .01 cent. This enables users to simply enter their data, and the transactions are paid for behind the scenes by the application. The user doesn't know they are using a sidechain, and the transaction costs are easy for Kauri to cover.

### More Information:

{% embed url="https://forum.poa.network/t/poa-network-and-kauri-announce-partnership-to-increase-access-to-information-in-the-ethereum-ecosystem/2935" %}







