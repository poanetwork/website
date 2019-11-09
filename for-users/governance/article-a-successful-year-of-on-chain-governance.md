---
description: POA自治过程和成功案例研究
---

# 文章：链上治理成功的一年

{% hint style="info" %}
本文最初于2019年3月发布。
{% endhint %}

2019年2月21日，第一份POA排放基金投票（ID：0）最终确定。 结果很接近。 八位验证者投票决定发送排放资金以支持POA基金会团队，九位投票者冻结资金直到下一个提案。 四个验证者选择不投票，这意味着**超过80％**的当前验证者参与了投票。

这是EmissionFunds的第一次投票，但这是通过POA链上治理流程提议并决定的第46次成功投票。 第一次投票于一年前，即2018年2月19日完成。该初始投票建议增加新的主网验证程序（Keys Ballot（ID：0），候选人以5比5的比例被否决）。

从那时起，添加了许多新的验证人，其他验证人已被拒绝或投票出去，并且已采取措施提高共识阈值（ConsensusBallot（ID：0），该验证人通过了8到7个）。 完整的投票列表可以在[https://voting.poa.network/poa-dapps-voting/](https://voting.poa.network/poa-dapps-voting/)上查看（将“网络”下拉列表设置为POA网络以进行查看）

一年多来，POA一直是一个完全自治的区块链。 与其他链上治理模型不同，POA的独特模型依赖于已知的，受信任的个人，他们使用同等的投票权来保护和服务于网络。

### 自治证明

POA Network的自治证明模型创建了一个公共的道德和负责任的治理体系。 在将网络验证人考虑为核心网络之前，必须先获得美国公证人许可证。 每个验证人都必须使用网络的“身份证明”[去中心化应用程序（DApp）](https://www.poa.network/for-validators/validator-dapps)来证明其身份和公证状态。

美国公证人有义务为签署正式文件提供公正可靠的证人。 他们确认当事方之间合同的合法性和完整性。 在POA网络中，每个验证者的信息（姓名，地址，公证许可）都是[公开可用](https://core-validators.poa.network/)的。 这种透明性强烈激励他们为网络的最大利益而努力。

为了使网络治理公平运行，这些验证人必须是自治个人，这一点很重要。 他们彼此不隶属，他们居住在美国的不同地区，从事不同的职业，并做出独立而明智的决定。

### 成为验证人

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

