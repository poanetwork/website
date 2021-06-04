---
description: POA Projects and the POA Network Roadmap for 2020-2021
---

# Roadmap

## POA Project Related Roadmaps

We are continuing to add new functionality and improve performance for our major applications. 

* [BlockScout Roadmap](https://docs.blockscout.com/about/roadmap)
* [TokenBridge Roadmap](https://docs.tokenbridge.net/about-tokenbridge/roadmap)

## **POA Network Roadmap**

## **2021 In Process**

{% hint style="info" %}
Additional items will be added as features are prioritized for deployment.
{% endhint %}

### **Berlin HF Migration**

**Target:** Q1 2021  
 ✅ **Completed**: POA Core: May 24, 2021 Block \#21,364,900

To maintain compatibility with Ethereum Mainnet, the Berlin Hard Fork will be activated on the POA Sokol Network and the POA Core network following a successful Ethereum migration. Berlin is currently scheduled for January on Ethereum, and will introduce the following EIPs:

1. EIP-2315: Simple Subroutines for the EVM
2. EIP-2929: Gas cost increases for state access opcodes

POA Sokol and Core will be supported by both OpenEthereum and Nethermind Clients.

### **EIP 1559 Implementation**

**Target:** Q2 2021

EIP 1559 introduces a `Base Fee` for all blockchain transactions. This is a minimum fee that is adjusted based on gas usage per block. When gas usage is high, the fee increases, and when it is low, the fee decreases. 

`Base fees` are burned by the protocol rather than paid directly to the miners \(or validators in the case of POA\). In addition to the base fee, a `priority fee` can be added to a transaction as a tip to incentivize POA validators to include it in a block.

EIP 1559 is an important change to Ethereum and POA Network will implement this change to maintain compatibility as well as be an early adopter of this improvement proposal.

### OpenEthereum Deprecation + Nethermind Implementation

 **Target:** Q2 2021

OpenEthereum has announced it will be deprecated and no longer supported by the team. The client will change to Erigon, formerly Turbo-geth, with no guarantees that it will support the POA network consensus. Due to this upcoming change, POA plans to shift to a Nethermind-only implementation. Validators and other node operators will need to migrate their nodes to the [Nethermind](https://nethermind.io/) client, details coming soon.

{% embed url="https://medium.com/openethereum/gnosis-joins-erigon-formerly-turbo-geth-to-release-next-gen-ethereum-client-c6708dd06dd" %}

### **AMB/OmniBridge implementation between POA and xDai**

**Target:** Q3 2021

To further POA interoperability and token usage, an Arbitrary Message Bridge and OmniBridge UI will be deployed between the POA Network and the xDai Chain. This will enable cross-chain transfers of POA and other tokens created on POA \(ERC20/ERC677 tokens\) between the POA network and xDai. POA native tokens and tokens created on POA can then be used on the xDai chain in applications such as the HoneySwap.

## **2020 Completed**

### **Istanbul Upgrade**

**Target:** Q1 2020  
 ****✅ **Status:** Completed Q4 2019

{% hint style="success" %}
**All Networks Successfully Activated**

* POA Sokol: Updated 12/05/2019 \| Block \#12095200
* POA Core: Updated 12/19/2019 \| Block\# 12598600
{% endhint %}

We have successfully upgraded the Kovan testnet to the latest Ethereum hard fork  **"**[Istanbul](https://eth.wiki/en/roadmap/istanbul)". This occurred on October 13, and we have not experienced any issues related to the update.

We will continue to monitor progress and are planning to update the Sokol testnet to Istanbul in the coming months.  This will not occur until after the Eth mainnet completes the Istanbul upgrade. We will inform all validators with instructions to ensure nodes are updated prior to the upgrade. Assuming the update on the testnet goes smoothly, we will coordinate the Istanbul fork on the POA Core network. 

### **On-Chain Randomness Activation**

**Target:** Q1 2020  
 ****✅ **Status:** Completed 2020

{% hint style="success" %}
**Activation Status**

* POA Sokol
  * Date Activated: 02/20/2020
  * Block \#: 13391641
  * Contract Address: 0x8f2b78169B0970F11a762e56659Db52B59CBCf1B
* POA Core: 
  * Date Scheduled: 03/31/2020
  * Block \#: 14350721
  * Contract Address: 0x67e90a54AeEA85f21949c645082FE95d77BC1E70
{% endhint %}

Randomness is vital to a blockchain and difficult to achieve within the protocol. We will introduce an on-chain RNG based on RANDAO, where validators use a commit/reveal strategy to create on-chain random numbers. Smart contracts will have access to this randomness without relying on third party applications or centralized RNGs. [More details here.](for-developers/on-chain-random-numbers/)

### **POA Games Fund \#2**

**Target:** Q2 2020  
 ****✅ **Status: Completed**

{% hint style="success" %}
We are currently accepting applications for our next round of funding. See [Grants for building on POA for more information](for-developers/grants-for-building-on-poa.md#poa-games-fund).
{% endhint %}

In 2019, the POA Games Fund has contributed funding to 4 games:

* \*\*\*\*[**Snailfarm**](https://www.stateofthedapps.com/dapps/poa-snailfarm)**:** A game where players buy resources which grow over time, in an endless virtuous loot loop. Learn more here: [https://medium.com/@thesnailking/the-next-great-frontier-for-snails-poa-ee7e2471bc51](https://medium.com/@thesnailking/the-next-great-frontier-for-snails-poa-ee7e2471bc51)
* \*\*\*\*[**Geon**](https://www.stateofthedapps.com/dapps/geon-app)**:** An augmented reality game where users collect Geon Coins from real world locations**.** One of the most [popular games deployed on **any** Ethereum Network](https://www.stateofthedapps.com/rankings/category/games) with hundreds of active daily users.
* \*\*\*\*[**DAOG**](https://daog.io/)**:** The 🐶DAOG is an open-ended governance game where emojis are controlled by smart contracts.  More info is available here: [https://medium.com/@austin\_48503/three-queens-b3760c33ab4b](https://medium.com/@austin_48503/three-queens-b3760c33ab4b)
* \*\*\*\*[**Clovers**](https://clovers.network)**:** The latest recipient of the games fund, Clovers is a scavenger hunt game where players search for certain types of clovers.

As these previously funded games continue to gain traction, we are initiating a second round of funding to encourage more games to build on POA. POA network provides an optimal solution for deploying games that require micro transactions, predictable fee structures, or accelerated transaction speeds.

### **POA Token Use Case Expansion**

**Target:** Q1 - Q4 2020  
 ****✅ **Status: POA Mania was created as an application used to stake POA tokens.**

We will continue to research and explore ways to expand POA token usage, adoption and use cases. This includes the possibility of creating a POA-based [stable token](for-users/use-cases-of-poa-token/stable-token.md), and exploring the ability to leverage POA as a [staking token](for-users/use-cases-of-poa-token/staking-token.md), either on its own or through a multi-collateral token basket.  To keep POA vital and growing, we must not only increase network adoption but also research the possibility of expanding usage beyond the network via the [TokenBridge](https://docs.tokenbridge.net/).

