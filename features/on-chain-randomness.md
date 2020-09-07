---
description: A RANDAO-like process creates reliable randomness on the POA Network
---

# On-Chain Randomness

Using a RANDAO-based Random Number Generator, validators on the POA Network produce random numbers on-chain. These random seeds are also available for usage by any smart contracts deployed to POA Network.

An example application that relies on random numbers is [POA Mania](../for-users/poa-mania/), a no-loss lottery which uses randomness to determine winners. Once a round completes, any user can close a round, which triggers a call to retrieve a random number and select a first, second and third place winner. However, rounds can only be closed during certain timeframes once a round is over. These timeframes correspond to a commit phase, when random numbers are committed to the chain by validators, and occur every 100 seconds. On-chain randomness is a 2 phase process, where validators commit numbers and later reveal them. To ensure that numbers are not known beforehand, contracts must restrict business logic to the commit phase.

![POA Mania use on-chain randomness to determine winners in a trustless and fair manner](../.gitbook/assets/poamania.png)

It is important for applications to use a trusted source of randomness, and 3rd party randomness may be subject to manipulation. Randomness is difficult to achieve on-chain, especially in a deterministic system, and POA's unique RNG is providing true, reliable randomness for applications

More information on how the POA RNG works is [available here.](on-chain-randomness.md)

