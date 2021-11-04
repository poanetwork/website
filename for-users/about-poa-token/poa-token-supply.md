---
description: POA emission schedule and current supply
---

# POA Token Supply

## **Current Total Supply**

Currently, 2 POA tokens are added per block. Each block is generated with an average time of 5 seconds, resulting in 6,307,200 blocks per year and an additional 12,614,400 POA tokens added to the total token supply per year.

Check the endpoint** **below for the up-to-date supply. Current circulating supply is also available at [CoinMarketCap](https://coinmarketcap.com/currencies/poa/).

{% hint style="success" %}
**Current Total Supply: ** [https://blockscout.com/poa/core/api?module=stats\&action=coinsupply](https://blockscout.com/poa/core/api?module=stats\&action=coinsupply)\
\
This API endpoint displays the total supply as a numerical value. Total supply is the **current number of coins in existence** (burned coins are not included).
{% endhint %}

### How Supply is Derived

At the onset of the network, the initial supply was 252,460,800 POA and 1 POA was created per block. Since November 2018 (Block 5329160), the POA emission fund was activated and an additional 1 token created per block. &#x20;

* For every block, 1 new POA token is created and distributed to the validator responsible for sealing that block.&#x20;
* Starting at block 5329160, an additional 1 POA token is created per block. Initially this amount was sent to the emission fund contract and the POA Foundation was set as the receiver of the emission fund.
* On May 9, 2020 Validators passed a vote to redistribute the emission fund, sending 0.5 POA to support POA Mania and 0.5 to the POA Foundation. The vote was enacted in block [15011232](https://blockscout.com/poa/core/blocks/15011232) ([see BlockScout transaction for details](https://blockscout.com/poa/core/tx/0xe7d562923ae3b0f3aa67b583a2c95e5f9fe0fc9a81a6c5f035b2b202914a7b3b/internal\_transactions)). Per-block emissions are now distributed accordingly:
  * 1 POA distributed to the sealing validator.
  * 0.5 POA accrued to POA Mania lottery proxy contract (0xD9505dc188d0f6dC583143e5A97D8e8cF7c107e0)&#x20;
  *   0.5 POA accrued to EmissionFunds address (0x517F3AcfF3aFC2fb45e574718bca6F919b798e10)



      More Details on this proposal: [https://forum.poa.network/t/proposal-to-support-poa-mania-with-a-block-reward-adjustment/3297/24](https://forum.poa.network/t/proposal-to-support-poa-mania-with-a-block-reward-adjustment/3297/24)

A total of **1,550,643** POA Tokens were burned when validators voted to burn the 3rd emission fund. These are not included in the total supply count. [More information available here](https://forum.poa.network/t/emission-funds-3-results/2957).

An amount of POA are locked in the POA20 bridge contract. This relates to circulating supply rather than total supply, and does not impact the current total supply amount. [This amount is available here](https://bridge.poa.net/statistics).

## Initial Supply

POA's initial token supply at Core network launch was **252,460,800 POA**. **70%** of total POA was reserved for the presale, and the remaining 30% reserved for Founders, Foundation/Legal and Partners/Advisors.

* **70%** or **176,722,560 POA** reserved for the token sale, all tokens were sold during the presale in 58 seconds.
* **20%** or **50,492,160 POA** reserved for Founders/Foundation/Legal. Initial lock for six months and released over two years. The final lock was completed December 15, 2019.
* **10%** or **25,246,080 POA** reserved for Partners and Advisors of POA Network.

{% hint style="info" %}
[The whitepaper](../whitepaper/poadao-v1/poa-network-functionality.md) has more information on POA token supply and emission mechanics.
{% endhint %}
