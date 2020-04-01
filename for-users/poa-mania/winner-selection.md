# Winner Selection

## POA Mania Prize Winners are selected in the following way:

1. An on-chain random number \(RN\) is collected when a round is closed. The RN value is between `0 - total deposit amount` . The RN is used to iterate through the list of active participants \(anyone with an active deposit when the round ends\).
2. The algorithm begins to move through the list of participants, comparing each participant’s deposit amount \(PN\) to the RN.
   1. Starting at the top of the list, if `PN < RN`, the participant is not the winner. PN is then subtracted from RN to create a new RN value \(`RN = RN-PN`\) .
   2. The algorithm moves to the next participant on the list, and compares their PN to the new RN.
   3. This continues until `PN > RN`. When this happens, this participant is declared the winner! They are removed from the list.
   4. The process restarts to select the 2nd and 3rd place winners.

3\) The selected winners receive their prizes and are returned to the active participant list as the next round begins.

## Jackpot Winner Selection

At the end of each round, 10% of the total prize pool is sent to a Jackpot. This amount accumulates until there is a winner, at which point it resets \(returns to 0\).  

In each round there is a 1% chance that any participant will win the jackpot. Odds are based on deposit amount, and follow the same procedures as above. However, the jackpot winner is not removed from the list, so it is possible that a jackpot winner may also win a prize in the same round.

