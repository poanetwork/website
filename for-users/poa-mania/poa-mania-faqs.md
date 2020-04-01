# POA Mania FAQs

## How do I deposit funds?

Connect a web3 wallet \(like [Nifty Wallet](https://chrome.google.com/webstore/detail/nifty-wallet/jbdaocneiiinmjbjlgalhcelgbejmnid), [Saturn Wallet ](https://chrome.google.com/webstore/detail/saturn-wallet/nkddgncdjgjfcddamfgcmfnlhccnimig?hl=de)or [MetaMask](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn)\)

Nifty and Saturn have built in POA support. For MetaMask, you will need to add the POA RPC endpoint. [Instructions here](https://www.poa.network/for-developers/getting-tokens-for-tests/sokol-testnet-faucet#metamask).

Click the deposit button and complete the transaction. You will see a link to the BlockScout tx and your pool balance will increase.

## How much do winners receive?

Winners split 84.5% of each pot. Of that amount, the breakdown is as follows:

* 50% 1st place winner
* 30% 2nd place winner
* 20% 3rd place winner

Odds of winning are increased by adding more POA to a pool.  Final winners are determined by a random number generated though the [on-chain RNG]().

## How do I close a round?

Press the `FINISH THE ROUND` button to close a round. This button is activated only after the countdown timer reaches 0:00:00:00. Once it reaches 0, rounds can be closed during the commit phase of the RNG. This happens every ~100 seconds and continues for 100 seconds. The round remains active and prizes continue to grow until a participant decides to press the button and close the round.

Whomever presses the button signs the transaction and pays the transaction fee. This person is known as the **Round Closer.** The Round Closer receives .5% of the total pot. The longer the pot grows, the higher prize the Round Closer will receive.

## What does "On-chain RNG reveal phase in progress" mean? Why can't I close the round now?

The on-chain randomness contract relies on a RANDAO-like process which proceeds in 40 block increments \(on the Sokol testnet\). During the first 20 blocks, validators commit random numbers to the chain, but they are not yet available to the protocol. During the second 20 blocks, these random numbers are revealed, undergo additional mathematical operations to increase entropy, and are made available.  

Depending on the block number, validators will either be in a commit or reveal phase. During a reveal phase, the revealing validator will know the next random number, so any business logic must be prohibited during this time. Rounds can only be closed during the commit phase. For more on the on-chain randomness process, see [https://www.poa.network/for-developers/on-chain-random-numbers](https://www.poa.network/for-developers/on-chain-random-numbers).   

## Why can't I withdraw or make a deposit?

Deposit and withdrawals are allowed during the majority of each round. **The exception is at the very end of each round**.  During the last ~3.5 minutes of a round a final RNG \(Random Number Generator\) commit/reveal phase is completed where deposits and withdrawals are not allowed. This restriction continues until the round is closed by a Round Closer.  Once the current round is closed, a new round starts and withdrawals and deposits are available again. 

## How do I win the jackpot?

Every round there is a 1% chance that the jackpot will have a winner. The winner is not removed from the round, so it is possible to win both the jackpot and a prize in the round. If no-one wins at the end of a round, the amount is carried over and 10% of the prize pool is added to the jackpot total. The jackpot resets once there is a winner.

