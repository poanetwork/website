# Accessing a Random Seed with a Smart Contract

The  [RandomAura](https://github.com/poanetwork/posdao-contracts/blob/master/contracts/RandomAuRa.sol) contract allows smart contracts to access a random number generated on-chain by the protocol.

The public getter `currentSeed` is used to access the network's random seed. Its value is only updated when the `revealNumber` function is called. This should occur **at least once per collection round**. The length in blocks of each collection round can be retrieved with the `collectRoundLength` public getter.

There are two phases in each round, a `commits phase` and a `reveals phase`. Since the revealing validator always knows the next random number before sending it, a DApp should prohibit business logic actions that depend on a random value during the `reveals phase`.

To determine the current phase, use `isCommitPhase` public getter: it will return `true` if the current block is in the `commits phase`, `false` if the block is in the `reveals phase`. To retrieve the number of the first block of the next `commits phase`, use the `nextCommitPhaseStartBlock` public getter. To do the same for `reveals phase`, use the `nextRevealPhaseStartBlock` public getter.

For example, a gambling application that relies on a random value should only allow bets to be placed during the `commits phase`.

## Example code to retrieve a random seed

Note: we are currently testing on Kovan and will provide a detailed example when the randomness contract is deployed.

```javascript
pragma solidity 0.5.16;


interface IPOSDAORandom {
    function collectRoundLength() external view returns(uint256);
    function currentSeed() external view returns(uint256);
}

contract Example {
    IPOSDAORandom private _posdaoRandomContract; // address of RandomAuRa contract
    uint256 private _seed;
    uint256 private _seedLastBlock;
    uint256 private _updateInterval;

    constructor(IPOSDAORandom _randomContract) public {
        require(_randomContract != IPOSDAORandom(0));
        _posdaoRandomContract = _randomContract;
        _seed = _randomContract.currentSeed();
        _seedLastBlock = block.number;
        _updateInterval = _randomContract.collectRoundLength();
        require(_updateInterval != 0);
    }

    function useSeed() public {
        if (_wasSeedUpdated()) {
            // using updated _seed ...
        } else {
            // using _seed ...
        }
    }

    function _wasSeedUpdated() private returns(bool) {
        if (block.number - _seedLastBlock <= _updateInterval) {
            return false;
        }

        _updateInterval = _posdaoRandomContract.collectRoundLength();

        uint256 remoteSeed = _posdaoRandomContract.currentSeed();
        if (remoteSeed != _seed) {
            _seed = remoteSeed;
            _seedLastBlock = block.number;
            return true;
        }
        return false;
    }
}
```

