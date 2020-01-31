# On-Chain Random Numbers

We are introducing an on-chain RNG based on RANDAO. It may be leveraged by smart contract developers to introduce random numbers into their applications. 

* [PRNG implementation explainer](prng-explainer.md)
* [How to access the random seed in a smart contract](accessing-a-random-seed-with-a-smart-contract.md)

{% hint style="success" %}
The following article explains on-chain randomness functions and how they will be used when POSDAO is implemented. It includes concepts and an example, and is a good place to start.

[https://forum.poa.network/t/reliable-randomness-bringing-on-chain-entropy-to-the-xdai-stable-chain/3015](https://forum.poa.network/t/reliable-randomness-bringing-on-chain-entropy-to-the-xdai-stable-chain/3015)
{% endhint %}

{% hint style="info" %}
 The current implementation requires a chain running Parity's AuRa consensus mechanism with version 2.7.1+. The Random Number generation contract was [introduced in this PR](https://github.com/paritytech/parity-ethereum/pull/10946).
{% endhint %}

