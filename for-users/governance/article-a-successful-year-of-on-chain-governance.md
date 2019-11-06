---
description: A look into POAs self-governance process and success
---

# Article: A Successful Year of On-Chain Governance

{% hint style="info" %}
This article was originally published in March, 2019.
{% endhint %}

On February 21st, 2019 the first POA EmissionFunds Ballot \(ID:0\) was finalized. The result was close; eight validators voted to send the emission funds to support the POA Foundation team, and nine voted to freeze the funds until the next proposal. Four validators chose not to vote, meaning that **more than 80%** of the current validators weighed in on the ballot.

While this was the first EmissionFunds ballot, it was the 46th successful ballot proposed and decided on through the POA on-chain governance process. The first ballot was finalized a year prior, on February 19, 2018. This initial ballot proposed the addition of a new mainnet validator \(Keys Ballot \(ID: 0\), the candidate was rejected five to one\).

Since that time, a number of new validators have been added, others have been rejected or voted out, and a measure has passed to increase the consensus threshold \(ConsensusBallot \(ID:0\), which passed eight to seven\). A full list of ballots can be viewed at [https://voting.poa.network/poa-dapps-voting/](https://voting.poa.network/poa-dapps-voting/) \(set the Network dropdown to POA Network to view\) 

For over a year, POA has functioned as a fully self-governed blockchain. Unlike other models of on-chain governance, POA’s unique model relies on known, trusted individuals who use their equal voting power to protect and serve the network.

### Proof of Autonomy

POA Network’s Proof of Autonomy model creates a public system of ethical and accountable governance. Network validators are required to obtain a US notary license before they are considered for the core network. Each validator must use the network’s “proof of identity” [decentralized applications \(DApps\)](../../for-validators/validator-dapps/) to prove their identity and notary status.

US notaries are duty-bound to provide impartial and trusted witness to the signing of official documents. They confirm the legality and integrity of contracts between parties. In the POA network, each validator’s information \(name, address, notary license\) is [publicly available.](https://core-validators.poa.network/) This transparency creates a strong incentive for them to work in the best interests of the network.

In order for network governance to operate fairly, it is important these validators are autonomous individuals. They are not affiliated with one another, they reside in different parts of the United States, are engaged in different professions, and make independent and informed decisions.

### Becoming a Validator

New validators are nominated and voted in by the current validators in the network. The process starts with an introduction in the [POA Forum](https://forum.poa.network/c/poa-core/notaries-intro). This forum provides an opportunity for transparent conversation; current validators \(and any other forum participants\) can ask questions of candidates in order to assess their interest in becoming a validator.

If a current validator approves of a candidate, they can nominate them to join the Sokol Test network as a validator. This network provides an opportunity for new validators to participate in consensus and ensure that they can successfully run a node and perform governance responsibilities before moving to the mainnet.

If they are successful, and all qualifications are met \(US Resident over 18, Notary Public, active participation in the testnet\), the Sokol validator may be nominated by a current mainnet validator to move to the POA core network. For those who have successfully become mainnet validators, the average time from forum introduction to POA mainnet validator [is approximately 125 days](https://forum.poa.network/t/poa-validators-candidates-guide/1250).

### Incentives and Accountability

Once elected and added as a node, validators receive 1 POA token plus transaction fees for every block they validate on the chain. When all nodes are functioning properly, a block is validated every 5 seconds. With 21 validators \(the current number, subject to change\) a validator receives @1 token \(+ fees\) every 105 seconds, or @822 tokens per 24 hour period.

This block reward incentivizes validators to maintain their nodes and participate in on-chain governance. If a node is corrupted in some way, or if a validator consistently fails to participate in governance \(this can be checked using the [poa-ballot-stats tool](https://github.com/poanetwork/poa-ballot-stats)\), a vote may be proposed by any validator to remove the non-compliant validator.

![ The poa-ballot-stats tool shows voting participation rates from 2018 average over 86%!](../../.gitbook/assets/ballot_voting.png)

It is the responsibility of all current validators to protect the network, and this includes monitoring their fellow validator nodes and resolving issues through the self-governance process.

While votes to update the POA protocol are cast on-chain, validators discuss the pros and cons beforehand in the POA forum. This platform provides the opportunity for an open dialogue where all community members can see and participate in the discussion. For example, the recent EmissionFunds Ballot was [debated for several weeks before the vote was initiated](https://forum.poa.network/t/first-round-of-poa-core-emission-funds-discussion-february-2019/1933).

### Securing the Network

Validators provide security for the POA network by maintaining the nodes that provide blockchain consensus. Consensus is required on all transactions to ensure the ledger is consistent and accurate across all nodes. Transactions are varied on the POA network, and include:

* **POA tokens as a medium of exchange:** Games like [DopeRaider](https://www.stateofthedapps.com/dapps/doperaider) use POA tokens for in game purchases and character actions. Players earn or lose POA based their choices in the game.
* **POA tokens to pay gas fees:** DApps such as [Geon](https://www.stateofthedapps.com/dapps/geon-app) use the POA core network to take advantage of low costs and high speeds. Users transact with Geon Coins; POA tokens are used to pay tx fees. [Communities in Kenya](https://www.bloomberg.com/news/features/2018-10-31/closing-the-cash-gap-with-cryptocurrency) are also using the POA Network to reduce transaction fees.
* **Bridged POA tokens:** Users can bridge POA to POA20 on the mainnet - then use POA20 as collateral for loans on [EthLend](https://ethlend.io/home), for merchant payments through [Coinpayments](https://www.coinpayments.net/), or as a way to arbitrage POA and POA20 on various market exchanges.

Validators are responsible for providing the blockchain nodes and security to facilitate these transactions in a fast and efficient way. When upgrades are required, validators propose on-chain ballots to maintain POA network functionality and integrity.

### Proposing a Ballot

Proposing a ballot is simple, and accomplished through the Governance DApp. This DApp supports the following ballot types:

* **Validator Management:** adding or removing validators, swapping validator keys.
* **Consensus Thresholds:** increasing or decreasing the number of votes required for a ballot to be approved.
* **Proxy Contracts:** modifying underlying smart contracts that constitute the network - may be utilized to update the network without a hard fork.
* **Emission Funds:** managing the emission funds - may be created every 3 months.

To create a ballot, a validator simply accesses the DApp, selects the ballot criteria \(description and end date\), and proposes it to the group. At the end of the ballot, the votes are tallied and the decision is enacted on the chain.

![Ballot DApp](../../.gitbook/assets/validator_ballot.png)

### Sustained Self-Governance

The POA on-chain governance model has worked for over a year to sustain and improve the network. Validators must be accountable to perform their duties, and this creates a high level of participation and engagement in the process. Because their identity is at stake, and voting participation is transparent, validator’s actions can be viewed and checked by the community that trusts the POA network to securely conduct and record transactions.

[Artis](https://artis.eco/en/), [Lukso](https://www.lukso.network/), [Ocean](https://blog.oceanprotocol.com/ocean-on-poa-vs-ethereum-mainnet-decd0ac72c97?gi=5704f5b58c5f), [Colu](https://www.colu.com/) and other protocols have witnessed the success of POA on-chain governance on the POA Core and have adopted it for their own networks and projects. In May 2019, the Kovan test network also adopted POA Governance tools. As we continue to improve POA's on-chain governance tools, we hope to see even more protocols adopt on-chain governance as a viable method to secure and maintain their chains.

{% hint style="success" %}
This article was moved from the POA forum: [https://forum.poa.network/t/a-successful-year-of-poa-on-chain-governance/2354](https://forum.poa.network/t/a-successful-year-of-poa-on-chain-governance/2354)
{% endhint %}

