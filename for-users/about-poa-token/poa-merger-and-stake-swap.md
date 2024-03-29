---
description: Feature to swap POA to STAKE
---

# POA Merger & STAKE Swap

{% hint style="success" %}
**POA Network Merger Announcement**

POA Network is entering a new phase as a valuable part of the xDai ecosystem! Over the next 6 months, POA users will have the opportunity to swap their POA for STAKE on xDai. &#x20;

Learn more about this opportunity and what it means for the future of POA and xDai below.
{% endhint %}

{% hint style="info" %}
Follow swap progress on [Dune Analytics](https://dune.xyz/maxaleks/POA-STAKE-merge).
{% endhint %}

{% hint style="info" %}
Go Directly to the [Swap Instructions](poa-merger-and-stake-swap.md#how-to-swap)
{% endhint %}

## Overview & Token Details

xDai provides a full-featured ecosystem with many tools POA users know (BlockScout, bridges) along with additional applications, DEXs, lending, games, and much more. The xDai community welcomes the expertise and experience of POA users and developers to the xDai chain.&#x20;

STAKE (as the name implies) is the staking token on xDai. With POSDAO staking, stakers can delegate stake to validators and earn rewards for helping protect the chain. STAKE is also used for voting on proposals. The community is active in proposal creation, discussion, and voting.&#x20;

STAKE is a popular token used throughout the xDai ecosystem including various [DeFi platforms](https://www.xdaichain.com/about-xdai/project-spotlights#defi), and can be bridged to and from Ethereum Mainnet as well as other chains easily with the OmniBridge application. On Ethereum, STAKE has additional applications, including the ability for users to stake and earn rewards through the [EasyStaking](https://easy-staking.xdaichain.com) application.

**->** [Learn more about STAKE here](https://www.xdaichain.com/for-stakers/stake-token).

**->** Questions about the merger? Ask in the [xDai discord poa channel.](https://discord.gg/mPJ9zkq)

{% hint style="info" %}
**STAKE on Exchanges:**

****[Ascendex](https://ascendex.com/en/global-digital-asset-platform) supports direct deposits and withdrawals of STAKE on xDai. To use with other exchanges, users can bridge tokens with the OmniBridge to the Ethereum Mainnet. &#x20;

Decentralized options for STAKE on xDai include [Sushiswap](https://sushi.com), [Honeyswap](https://honeyswap.org), [Swapr](https://swapr.eth.link/#/pools?chainId=1) and many more. [See the complete list](https://www.xdaichain.com/about-xdai/project-spotlights#defi).
{% endhint %}

## Swap Details

Swaps are available at a set price of **466.6163443 POA per 1 STAKE**. This price was derived using a TWAP (Time-weighted Average Price) for the 2 tokens between October 21, 2021 and November 3, 2021.&#x20;

![](../../.gitbook/assets/stake-poa.png)

The swap contract will launch with the ability for users to exchange 20% of POA tokens in circulation (58,672,514). Demand will be evaluated at regular intervals and additional STAKE added in batched amounts as required to cover POA to STAKE swaps.&#x20;

The swap program will be active with the same terms for 6 months, **starting on November 4, 2021 and ending on May 5, 2022**. POA holders will have the opportunity to swap at any time during this period without changes to the set price. Swaps are 1 way, there is no ability to swap STAKE back to WPOA through the application.&#x20;

During the 6 month swapping window, POA users may continue to earn rewards on POA Mania on the POA Network. However, **on May 5, 2022, POA rewards will cease for POA Mania players and swapping will no longer be available.**&#x20;

Following emission & swapping cessation, POA network will continue to function in an important stress-testing capacity for users and developers. Client upgrades, testing, and experimentation will be conducted on POA prior to deployment on xDai or other chains using the POA network.

## How to Swap

### Video

{% embed url="https://www.youtube.com/watch?v=7CCtA1Rl66g" %}

### Instructions

Swapping from POA on POA Network to STAKE on xDai is a 2 step process. Steps detailed below.

1.  **Bridge POA from the POA Network to the xDai Network using the OmniBridge**. During bridging, POA is converted to WPOA (wrapped POA) on the xDai chain.

    [omni.xdaichain.com/bridge](http://omni.xdaichain.com/bridge)
2.  **WPOA on xDai is swapped for STAKE on xDai using the swap application.**

    [https://poa-to-stake.poa.network/](https://poa-to-stake.poa.network)

{% hint style="warning" %}
We recommend running through this process the first time using a small amount of POA (like 1-5 POA). Gas prices between POA and xDai are very inexpensive, so it is worth it do a test run first to understand and make sure everything works.
{% endhint %}

## 1. Bridge POA to WPOA on xDai

{% hint style="info" %}
Do you need to withdraw your POA tokens from Binance?  [Start here](poa-stake-faqs.md#im-having-trouble-moving-poa-out-of-binance)
{% endhint %}

{% hint style="warning" %}
Having issues? [See the FAQs](poa-stake-faqs.md)
{% endhint %}

### 1) **Connect and Initiate Bridge Transaction**

Best option is to use MetaMask, these instructions do not support TrustWallet. The easiest way to start is to create a MetaMask account and send funds to that account from Trustwallet to complete the swap.

1. Go to [omni.xdaichain.com/bridge](http://omni.xdaichain.com/bridge)
2. **Connect your web3 wallet** (in this example we use MetaMask) **to the POA Network**.   If you need to add POA Network to MetaMask custom networks, [instructions are here](../wallets/metamask.md#poa-core). Select the **POA-XDAI Bridge** in the bridge selector dropdown.
3. Enter the **amount of POA** you want to bridge to WPOA. Note you need to reserve a very small amount to pay for gas.
4. Wrapped POA (WPOA) you will receive on xDai. 3 and 4 should match.

Click **Transfer** to start. (_note: this will transfer to **your same wallet address on the xDai chain**. If you want to send to a different address on the xDai chain, you can use the Advanced feature. Be sure to **triple check if you choose this option**, as funds sent to the wrong address may not be recoverable_).

![](../../.gitbook/assets/poa-1.png)

### 2) **Continue Transfer**

![](../../.gitbook/assets/wpoa-2.png)

### 3) **Confirm in MetaMask**

![](../../.gitbook/assets/wpoa-3.png)

### 4) **Wait for Confirmation**

You can view progress on the ALM monitor. The transfer should only take a few minutes to process between POA Network and the xDai Chain.

![](../../.gitbook/assets/wpoa-4.png)

### 5) **Add Balance to xDai Wallet (optional)**

The following processes detail adding WPOA to your wallet. You can also confirm the transfer in Blockscout by pasting your address in the search bar and checking your tokens balance.&#x20;

{% hint style="info" %}
&#x20;If you don't want to add WPOA to view in your wallet, skip to [section 2 swap WPOA to STAKE](poa-merger-and-stake-swap.md#1.-bridge-poa-to-wpoa-on-xdai-1).
{% endhint %}

Here we use Metamask as an example.

1. Switch to the xDai Network ([How to add xDai network to your MetaMask](https://www.xdaichain.com/for-users/wallets/metamask/metamask-setup))
2. Go to Assets
3. Press Import Tokens

![](<../../.gitbook/assets/MM 1-3.png>)

1.  Add the WPOA Token Contract Address `0x9fe3864F9Ae7cfb5668Dae90C0e20c4C3D437664`

    The remaining info should autopopulate.&#x20;
2. Press **Add Custom Token**.

&#x20;![](../../.gitbook/assets/import-2.png)

You should now see WPOA along with your balance.&#x20;

1. Press **Import Tokens** to finalize&#x20;
2. You will now see the amount of WPOA in your balance

![](../../.gitbook/assets/import-3.png)

## 2. Swap WPOA to STAKE on the xDai Network

### 1) **Go to swap application at** [**https://poa-to-stake.poa.network/**](https://poa-to-stake.poa.network)**.**&#x20;

Press **Connect wallet**.

![](../../.gitbook/assets/swap-1.png)

### 2) **Select your wallet application of choice.**&#x20;

In this example we use MetaMask connected to the xDai Chain. **Note you must have MetaMask enabled in your extensions to see this option.**&#x20;

![](../../.gitbook/assets/swap-2.png)

### 3) **Enter the amount you want to swap, or Convert All to swap all.**&#x20;

_You will need a small amount of xDai to process the transaction. You can get some at the community faucet at_ [_https://xdai-app.herokuapp.com/faucet_](https://xdai-app.herokuapp.com/faucet)__

![](../../.gitbook/assets/swap-3.png)

### 4) _****_** Confirm the Transaction in MetaMask**

![](../../.gitbook/assets/swap-4.png)

### 5) **Transaction is initiated and should be completed shortly.**&#x20;

From this final screen you can:

1. **View progress in BlockScout**: Click Check the status here to see swap progress.
2. **Add STAKE to MetaMask**: Click to add the STAKE token to your MetaMask wallet.

![](../../.gitbook/assets/swap-5.png)

## Additional Details from BlockScout

{% hint style="info" %}
WPOA to STAKE Swap Contract on xDai: [https://blockscout.com/xdai/mainnet/address/0x2A8475c74b7A9E08DB6dfdcb5f58AC53B598B319/transactions](https://blockscout.com/xdai/mainnet/address/0x2A8475c74b7A9E08DB6dfdcb5f58AC53B598B319/transactions)

\
WPOA Address on xDai: [https://blockscout.com/xdai/mainnet/token/0x9fe3864F9Ae7cfb5668Dae90C0e20c4C3D437664/token-transfers](https://blockscout.com/xdai/mainnet/token/0x9fe3864F9Ae7cfb5668Dae90C0e20c4C3D437664/token-transfers)

\
STAKE Address on xDai: [https://blockscout.com/xdai/mainnet/token/0xb7D311E2Eb55F2f68a9440da38e7989210b9A05e/token-transfers](https://blockscout.com/xdai/mainnet/token/0xb7D311E2Eb55F2f68a9440da38e7989210b9A05e/token-transfers)

\
BlockScout Tx of example WPOA to STAKE swap: [https://blockscout.com/xdai/mainnet/tx/0x36c282174dc10c002c3d38f657c5d951279ce3fd6b905e95402485649f7656f3](https://blockscout.com/xdai/mainnet/tx/0x36c282174dc10c002c3d38f657c5d951279ce3fd6b905e95402485649f7656f3)
{% endhint %}

{% hint style="warning" %}
If you are having difficulties, [see the FAQs](poa-stake-faqs.md)
{% endhint %}
