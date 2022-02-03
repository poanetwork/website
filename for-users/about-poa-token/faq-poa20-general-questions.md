---
description: General questions related to POA20
---

# FAQ: POA20 General Questions

## Table of contents

* [What is the POA20 Bridge?](faq-poa20-general-questions.md#what-is-the-poa20-bridge)
* [What is POA20?](faq-poa20-general-questions.md#what-is-the-poa20-bridge)
* [Do I have to transform my POA native tokens to POA20?](faq-poa20-general-questions.md#do-i-have-to-transform-my-poa-native-tokens-to-poa-20)
* [What is the purpose of having a POA20 token?](faq-poa20-general-questions.md#what-is-the-purpose-of-having-a-poa20-token)
* [Will the supply of POA tokens increase as a result of POA20 tokens?](faq-poa20-general-questions.md#will-the-supply-of-poa-tokens-increase-as-a-result-of-poa20-tokens)
* [What is the difference between POA native token and POA20 token?](faq-poa20-general-questions.md#what-is-the-difference-between-poa-native-token-and-poa20-token)
* [How do I transform my POA native tokens to POA20 tokens?](faq-poa20-general-questions.md#how-do-i-transform-my-poa-native-tokens-to-poa20-tokens)
* [Has the contract code for the POA20 Bridge been audited?](faq-poa20-general-questions.md#has-the-contract-code-for-the-poa20-bridge-been-audited)
* [Is there a limit on how many POA native tokens can be bridged over to become POA20 tokens?](faq-poa20-general-questions.md#is-there-a-limit-on-how-many-poa-native-tokens-can-be-bridged-over-to-become-poa20-tokens)
* [Is there a minimum or maximum amount of tokens per wallet that can be transferred via the POA20 Bridge?](faq-poa20-general-questions.md#is-there-a-minimum-or-maximum-amount-of-tokens-per-wallet-that-can-be-transferred-via-the-poa20-bridge)
* [What are the fees for converting POA native tokens to POA20 tokens and vice-versa? Who will be paying these fees?](faq-poa20-general-questions.md#what-are-the-fees-for-converting-poa-native-tokens-to-poa20-tokens-and-vice-versa-who-will-be-paying-these-fees)
* [How many confirmations are required to convert the POA20 tokens to POA native tokens and vice-versa?](faq-poa20-general-questions.md#how-many-confirmations-are-required-to-convert-the-poa20-tokens-to-poa-native-tokens-and-vice-versa)
* [Where can I find more information about POA20 Bridge source code](faq-poa20-general-questions.md#where-can-i-find-more-information-about-poa20-bridge-source-code)?

## What is the POA20 Bridge?&#x20;

The POA20 Bridge is an interoperability protocol which allows users to convert their own POA Native Tokens from the POA Network onto the Ethereum network in a quick and cost-efficient manner

This new interoperability technology opens up a whole new avenue of solutions for POA users.

{% hint style="success" %}
**To convert your POA to POA20, vist the UI at** [**https://bridge.poa.net/**](https://bridge.poa.net)****
{% endhint %}

## What is POA20?&#x20;

POA20 is an ERC20 representation of POA native tokens on Ethereum network. The POA20 token displays the exact same properties as the standard ERC20 token and allows it to be used in all the same places that offer ERC20 compatibility.

[https://youtu.be/fWopyXl3VhQ](https://youtu.be/fWopyXl3VhQ)

## Do I have to transform my POA native tokens to POA20?&#x20;

No, you do not need to transform your POA native tokens. POA native tokens are used to execute smart contracts on the POA Network, which is a faster and more cost-efficient than Ethereum network. Developers creating DApps on the POA Network will **need** POA native tokens in order for their DApps to function on the POA Network.

## What is the purpose of having a POA20 token?&#x20;

POA20 Tokens are minted to prove cross chain bridges can work in a safe and secure manner with 2 standalone blockchains. We believe the interoperability technology we’ve been able to develop helps open up a whole new avenue of solutions that can be offered to our users. By connecting blockchains with these bridges you allow for a variety of new use cases that never existed before. POA Network truly believes cross chain bridges is a critical step in the right direction as we aim to solve the problem of scalability and connectivity.

## Will the supply of POA tokens increase as a result of POA20 tokens?&#x20;

**No!** It’s important to note that there will be **no increase** in the POA tokens. The existing amount of **circulating POA tokens will stay the same** and simply be **distributed across 2 networks** (POA Network & Ethereum network) instead of 1 (POA Network) and this is cryptographically auditable.

## What is the difference between POA native token and POA20 token?

POA native tokens live on the POA Network whereas ​POA20 tokens live on the Ethereum network.

## What is the POA20 token Contract Address, Symbol, and # of Decimal Places in order to add it as a Custom Coin on MyEtherWallet?

The symbol is POA20. The number of Decimal places is 18. The smart contract address is [0x6758B7d441a9739b98552B373703d8d3d14f9e62](https://etherscan.io/token/0x6758B7d441a9739b98552B373703d8d3d14f9e62)

## How do I transform my POA native tokens to POA20 tokens?&#x20;

The POA20 Bridge is a public DApp users can access with [Metamask](https://github.com/poanetwork/wiki/wiki/POA-Network-on-MetaMask). A user can send POA native tokens and receive an equivalent amount of POA20 tokens on the Ethereum network. By toggling the network on Metamask, you’re also able to transfer the other way around and send POA20 tokens to receive POA native tokens.

## Has the contract code for the POA20 Bridge been audited?&#x20;

We have had 4 different independent security audits of bridge contracts, including a smart contract audit, security assessment, and a legal review. Those security audits will be published before the launch of the POA20 Bridge.

#### Smart contracts security audits for Native to ERC20 bridge:

[Blockchain Labs](https://www.blockchainlabs.nz) "Audit report for POA Parity Bridge Contracts"

* [https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/tree/audit/audit](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/tree/audit/audit)

[LevelK](http://levelk.io) "Audit for POA20 Bridge"

* [https://github.com/levelkdev/audits/blob/master/POA-Bridge/POA-Bridge-Audit.pdf](https://github.com/levelkdev/audits/blob/master/POA-Bridge/POA-Bridge-Audit.pdf)

[MixBytes](https://mixbytes.io) "Audit of bridge smart contracts in the POA Network project"

* [https://github.com/mixbytes/audits\_public/blob/master/solidity/POANetwork/audit\_en.md](https://github.com/mixbytes/audits\_public/blob/master/solidity/POANetwork/audit\_en.md)

[Digital Security](https://dsec.ru) "Report on the results of the security assessment PoA.network cross-chain bridge"

* [https://github.com/DSecurity/public-audit-reports](https://github.com/DSecurity/public-audit-reports)

#### Smart contract audits for ERC20 to ERC20 bridge:

[PepperSec](https://peppersec.com) "POA Network bridge's smart contracts audit"

* [https://github.com/peppersec/public-audit-reports](https://github.com/peppersec/public-audit-reports)

#### Security Assesment for Native to ERC20 bridge:

[Secureware](http://secureware.io) "POA20 Bridge security assessment"

* [https://github.com/secureware/reports/blob/master/POA\_Network-POA\_Bridge\_Security\_Assessment.pdf](https://github.com/secureware/reports/blob/master/POA\_Network-POA\_Bridge\_Security\_Assessment.pdf)

#### Legal memorandum for Native to ERC20 bridge:

* Federal Money Transmitting Laws as Applied to Bridge by Harris, Wiltshire & Grannis LLP [2018\_05\_04\_Bridge\_money\_transmission.pdf](https://forum.poa.network/uploads/short-url/jm5ndHjTeFcV5Mx2sCk2U6yWVbC.pdf)

Please contact [info@poa.network](mailto:info@poa.network) with inquiries about legal review

## **If I sell my POA20 tokens, what happens to my native POA tokens?**

Upon receiving your POA20 tokens you no longer own your native POA tokens. The moment you use the bridge to send them to the Ethereum network, they are locked up and stored in the contract address. Thus you effectively have no native POA tokens on the POA Network and now have POA20 tokens on the Ethereum network.

## Is there a limit on how many POA native tokens can be bridged over to become POA20 tokens?&#x20;

There is no limit, however, there is a daily quota. Hypothetically the entire circulating supply can be bridged, though this likely will never happen since there will be strong use cases to use the tokens on either network.

#### Daily quota:

| Operation                | Quota           |
| ------------------------ | --------------- |
| Daily limit POA -> POA20 | 3,000,000 POA   |
| Daily limit POA20 -> POA | 1,500,000 POA20 |
| Maximum per tx POA       | 1,500,000 POA   |
| Maximum per tx POA20     | 1,500,000 POA20 |
| Minimum per tx POA       | 300 POA         |
| Minimum per tx POA20     | 750 POA20       |

## Is there a minimum or maximum amount of tokens per wallet that can be transferred via the POA20 Bridge?&#x20;

The minimum amount of POA native tokens to transfer to the Ethereum main network is **300 POA native tokens** . The minimum amount in transferring POA20 to POA Network is **750 POA20 tokens**.

Since POA Network is sponsoring the fees for the transfer through the bridge, we wanted to impose a minimum amount of tokens to transfer. We calculated the minimum amount of tokens to transfer based on the fees that POA Network is sponsoring.

## What are the fees for converting POA native tokens to POA20 tokens and vice-versa? Who will be paying these fees?&#x20;

POA Network is paying and sponsoring the fees for the multiple transactions during the trial period. This will change after the trial period is complete. Users will need to pay a small amount of gas fee when using Metamask for to submit their transactions.

## How many confirmations are required to convert the POA20 tokens to POA native tokens and vice-versa?&#x20;

There will 15 confirmations. On the POA mainnet and 15 confirmations on the Ethereum network. On Sokol testnet and Kovan testnet, the test bridge will have 2 confirmations.

## Where can I find more information about POA20 Bridge source code?

* Github: [https://github.com/poanetwork/tokenbridge](https://github.com/poanetwork/tokenbridge)
* [TokenBridge Documentation](https://docs.tokenbridge.net)
