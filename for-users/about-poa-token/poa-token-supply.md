---
description: POA emission schedule and current supply
---

# POA Token Supply

## **Current Total Supply**

Currently, 2 POA tokens are added per block. Each block is generated with an average time of 5 seconds, resulting in 6,307,200 blocks per year and an additional 12,614,400 POA tokens added to the total token supply per year.

Check the endpoint ****below for the up-to-date supply.

{% hint style="success" %}
**Current Total Supply:**  [https://blockscout.com/poa/core/api?module=stats&action=coinsupply](https://blockscout.com/poa/core/api?module=stats&action=coinsupply)  
  
This API endpoint displays the total supply as a numerical value. Total supply is the **current number of coins in existence** \(burned coins are not included\).
{% endhint %}

### How Supply is Derived

Currently, 2 POA are created per block. At the onset of the network, the initial supply was 252,460,800 POA and 1 POA was created per block. Since November 2018 \(Block 5329160\), the POA emission fund was activated and an additional 1 token created per block.  

* For every block, 1 new POA token is created and distributed to the validator responsible for sealing that block. The sum of the total blocks created to date = the amount of POA created as validator rewards.
* Since block 5329160, and additional 1 POA token is created per block and sent to the emission fund contract. Currently, the POA Foundation is set as the receiver of the emission fund. 

A total of **1,550,643** POA Tokens were burned when validators voted to burn the 3rd emission fund. These are not included in the total supply count. [More information available here](https://forum.poa.network/t/emission-funds-3-results/2957).

An amount of POA are locked in the POA20 bridge contract. This relates to circulating supply rather than total supply, and does not impact the current total supply amount. [This amount is available here](https://bridge.poa.net/statistics).

## Initial Supply

POA's initial token supply at Core network launch was **252,460,800 POA**. **70%** of total POA was reserved for the presale, and the remaining 30% reserved for Founders, Foundation/Legal and Partners/Advisors.

* **70%** or **176,722,560 POA** reserved for the token sale, all tokens were sold during the presale in 58 seconds.
* **20%** or **50,492,160 POA** reserved for Founders/Foundation/Legal. Initial lock for six months and released over two years. The final lock was completed December 15, 2019.
* **10%** or **25,246,080 POA** reserved for Partners and Advisors of POA Network.

{% hint style="info" %}
[See the whitepaper ](../whitepaper/poadao-v1/poa-network-functionality.md)for more information on POA token supply and emission mechanics.
{% endhint %}

