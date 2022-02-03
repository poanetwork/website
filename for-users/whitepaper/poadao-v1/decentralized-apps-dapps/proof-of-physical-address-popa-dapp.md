# Proof of Physical Address (PoPA) DApp

## Proof of Physical Address (PoPA) DApp

Using Proof of Physical Address, a user can confirm his/her physical address. It can be used to prove residency.

### **Typical workflow for Identity DApps on PoPA example**

![ Click on Image to Enlarge: User fills out a form in DApp and submits it to the server.](../../../../.gitbook/assets/proof-of-address.png)

Server consists of a web app and a **** Parity node connected to the blockchain. The node is run under the Ethereum account that was used to deploy the PoPA contract (contract's `owner`), and this account needs to be unlocked. It shouldn't have any ether on it though, as it doesn't send any more transactions.

Server validates and normalizes the user's input: removes trailing spaces, converts letters to lower case. Then it generates a random confirmation code (alphanumeric sequence) and computes its SHA-3 (strictly speaking, keccak256) hash. Also, it generates a random session code (see below), that it stores in memory/database along with the user's eth address and plain text confirmation code. Then the server combines input data, namely `str2sign = (user's eth address + user's name + all parts of physical address + confirmation code's hash)`into a string that is hashed and signed with the `owner`'s private key. \
(This is why the `owner`'s account needs to be unlocked. In the next release of web3js it will probably become possible to sign using a private key without unlocking.)

Signature, the confirmation code's hash, the user's normalized input, and the session code are sent back to the client. User then confirms the transaction in MetaMask and invokes the contract's method. The contract combines input data in the same order as the server did, hashes it, and then uses the built-in function `ecrecover` to validate that the signature belongs to the `owner`. If it doesn't, the contract rejects the transaction, otherwise it adds some metadata, most importantly the current block's number, and saves it in the blockchain.

When the transaction is mined, `tx_id` is returned to the client and then via the client to the server, along with the session code. Server queries memory by the session code and validates the user's eth address. Then it fetches the transaction from the blockchain by `tx_id`. It verifies that `tx.to` is equal to `owner` and `tx.from` is equal to the user's eth address. Then, using `tx.blockNumber` the server uses the contract's method to find the physical address added at that blockNumber. User should be limited to registering at most one address per eth block. Since block generation time is less than a minute, it shouldn't be too restrictive on the user.

Having fetched the address from the contract, the server calls postoffice's api (lob.com) to create a postcard. Server uses the session code to get plain text confirmation code from memory and print it on the postcard. Then the server removes this session code from memory to prevent reuse.

When the postcard arrives, the user enters the confirmation code in DApp, DApps gets signature from the server and invokes the contract's method. Contract verifies signature, computes the confirmation code's hash and loops over the user's addresses to find the matching one.

### Possible cheating:&#x20;

1. _user can generate his/her own confirmation code, compute all hashes and submit it to the contract, and then confirm it_ This can't be done because the user doesn't know the `owner`'s private key and therefore can't compute a valid signature.&#x20;
2. _user can reuse someone else's confirmation code, or his/her own confirmation code from one of the previously confirmed addresses_ This is prevented by hashing all essential pieces of data together before signing (user's eth address, full physical address, confirmation code) and by checking the address for duplicates in the contract.&#x20;
3. _user can submit the form, but doesn't sign the transaction_ For this reason the postcard is sent after the address is added to the blockchain and `tx_id` is presented to the server.&#x20;
4. _user can submit the form and sign the transaction, but sends another address to the server to send postcard to_ After the first transaction is mined, the server sees for itself what address was added and fetches it from the contract instead of trusting the client. Session code is then used to retrieve the corresponding confirmation code. To simpify things, we can limit the user to only submitting a single address per block. In this case, the contract just needs to find the first record with matching `creation_block`
5. _user can resubmit the same tx\_id to the server multiple times_ This is prevented by removing the session code from memory after the first postcard is sent.
