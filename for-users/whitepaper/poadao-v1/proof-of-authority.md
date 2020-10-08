# Proof of Authority

### AuthorityRound \(AuRa\)

Aura is one of the Blockchain consensus algorithms available in OpenEthereum \(previously Parity\). It is capable of tolerating up to 50% of malicious nodes with chain reorganizations possible up to a limited depth, dependent on the number of validators, after which finality is guaranteed. This consensus requires a set of validators to be specified, which determines the list of blockchain addresses which participate in the consensus at each height. Sealing a block is the act of collecting transactions and attaching a header to produce a block.

At each step the primary node is chosen that is entitled to seal and broadcast a block, specifically `step modulo #_of_validators`the validator is chosen from the set. Blocks should be always sealed on top of the latest known block in the canonical chain. The block's header includes the step and the primary's signature of the block hash.

Block can be verified by checking that the signature belongs to the correct primary for the given step. Finality of the chain can be achieved within at most `2 x #_of_validator` steps, after more than 50% of the nodes are signed on a chain and then they are signed again on those signatures. 

### History of POA

On March 6, 2017, a group of blockchain companies announced new blockchain based on Ethereum protocol with Proof of Authority consensus . Spam attack on the Ropsten testnet was the reason to create a new public test network. This network was named Kovan, for a metro station in Singapore, where companies who founded the network are located. It is a common name convention for Ethereum test networks, for example, Morden, Ropsten, and Rinkeby are names of metro stations.

### Adoption of Kovan blockchain

In the table below we show stats for Main \(Homestead\) and Test \(Kovan\) Ethereum networks.

| Network | Type | Blocks mined | Tx created | Contract created | Accounts created |  |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Kovan | Testnet | 3,417,527 | 2,859,549 | 54,384 | 18,082 | Text |
| Homestead | Mainnet | 4,203,319 | 50,374,359 | 1,488,072 | 4,957,479 | Text |

Large numbers of transactions, smart contracts, and accounts on the test network show adoption from the community and proven utility benefit.

