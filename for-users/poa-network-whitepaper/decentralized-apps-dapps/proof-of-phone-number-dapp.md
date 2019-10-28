# Proof of Phone Number DApp

![Click on image to enlarge](../../../.gitbook/assets/pona.png)

User fills out a form in DApp providing his/her phone number and submits it to the server.

Server consists of a web app and a parity node connected to the blockchain. The node is run under the ethereum account that was used to deploy the PoP contract \(contract's `owner`\). This account needs to be unlocked.

Server validates and normalizes the user's phone number: removes trailing spaces, converts it to international format.

Then it generates a random confirmation code \(alphanumeric sequence\) and computes its SHA-3 \(strictly speaking, keccak256\) hash. Also, it generates a random session code \(see below\) that it stores in memory/database along with the user's eth address and plain text confirmation code. Then the server combines input data, namely `str2sign = (user's eth address + user's phone number + confirmation code's hash`\) into a string that is hashed and signed with the `owner`'s private key \(this is why `owner`'s account needs to be unlocked\).

Signature, the confirmation code's hash, the user's normalized phone number, and the session code are sent back to the client. User then confirms the transaction in MetaMask and invokes the contract's method. The contract combines input data in the same order as the server did, hashes it, and then uses the built-in function `ecrecover` to validate that the signature belongs to the `owner`. If it doesn't, the contract rejects the transaction, otherwise it adds some metadata, most importantly the current block's number, and saves it in the blockchain.

When the transaction is mined, `tx_id` is returned to the client and then via the client to the server along with session code. Server queries memory by the session code and validates the user's eth address. Then it fetches the transaction from the blockchain by `tx_id`. It verifies that `tx.to` is equal to `owner` and `tx.from` is equal to the user's eth address. Then, using `tx.blockNumber` the server uses the contract's method to find the phone number added at that blockNumber. User should be limited to registering at most one phone number per eth block.

Then the server uses the session code to get plain text confirmation code from memory and send it via SMS service \(twilio.com\) to the user's phone number. Then the server removes the session code from memory to prevent reuse.

Having received SMS with verification code, the user returns to the DApp and confirms the transaction in MetaMask, which sends confirmation code to the contract's method directly, without calling the server. There doesn't seem to be any need for signing this transaction with the `owner`'s private key. Contract computes the confirmation code's hash and loops over the user's phone numbers to find a matching one.

## Possible cheating

1. _user can generate his/her own confirmation code, compute all hashes and submit it to the contract, and then confirm it_ This can't be done because the user doesn't know the `owner`'s private key and therefore can't compute a valid signature.
2. _user can reuse someone else's confirmation code, or his/her own confirmation code from one of the previously confirmed phone numbers_ This is prevented by hashing all essential pieces of data together before signing \(user's eth address, phone number, confirmation code\) and by checking the phone number for duplicates in the contract.
3. _user can submit the form, but doesn't sign the transaction_ For this reason, SMS is sent after the phone number is added to the blockchain and `tx_id` is presented to the server.
4. _user can submit the form and sign the transaction, but sends another phone number to the server to send SMS to_ After the first transaction is mined, the server sees for itself what phone number was added and fetches it from the contract instead of trusting the client. Session code is then used to retrieve the corresponding confirmation code. To simpify things, we can limit the user to only submitting a single phone number per block. In this case the contract just needs to find the first record with matching `creation_block`.
5. _user can resubmit the same tx\_id to the server multiple times_ This is prevented by removing the session code from memory after the first postcard was sent.

