# On-Chain Random Numbers

We are introducing an on-chain RNG based on RANDAO. It may be leveraged by smart contract developers to introduce random numbers into their applications.  _Note that random numbers are limited to certain blocks in the current implementation. See below for more information._

* [PRNG implementation explainer](prng-explainer.md)
* [How to access the random seed in a smart contract](accessing-a-random-seed-with-a-smart-contract.md)
* [Randomness FAQs](randomness-faqs.md)

{% hint style="success" %}
The following article explains on-chain randomness functions and how they will be used when POSDAO is implemented. It includes concepts and an example, and is a good place to start.

[https://forum.poa.network/t/reliable-randomness-bringing-on-chain-entropy-to-the-xdai-stable-chain/3015](https://forum.poa.network/t/reliable-randomness-bringing-on-chain-entropy-to-the-xdai-stable-chain/3015)
{% endhint %}

## Randomness Contract \(RandomAuRa\) 

{% tabs %}
{% tab title="POA Core" %}
| Block | Date | Contract |
| :--- | :--- | :--- |
| 14350721 | 03/31/2020 | 0x67e90a54AeEA85f21949c645082FE95d77BC1E70 |
{% endtab %}

{% tab title="POA Sokol \(Testnet\)" %}
| Block | Date | Contract |
| :--- | :--- | :--- |
| 13391641 | 02/20/2020 | 0x8f2b78169B0970F11a762e56659Db52B59CBCf1B |
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The current implementation requires a chain running Parity's AuRa consensus mechanism with version 2.7.2+. The Random Number generation contract was [introduced in this PR](https://github.com/paritytech/parity-ethereum/pull/10946).
{% endhint %}

