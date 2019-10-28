# Proof of Social Network DApp

![Click on image to enlarge](../../../.gitbook/assets/posn.png)

User fills out a form in DApp providing the link to his/her social network profile and submits it to the server.

Server consists of a web app and a parity node connected to the blockchain. The node is run under the ethereum account that was used to deploy the PoSN contract \(contract's `owner`\). This account needs to be unlocked.

Server validates and normalizes the user's profile link: removes trailing spaces, converts protocol to HTTPS if applicable, domain name to lowercase, and removes extra URL parameters.

Then it generates a random confirmation code \(alphanumeric sequence\) and computes its SHA-3 \(strictly speaking, keccak256\) hash. Also, it generates a random session code \(see below\), that it stores in memory/database along with the user's eth address and plain text confirmation code. Then server combines input data, namely `str2sign = (user's eth address + user's profile link + confirmation code's hash`\) into a string that is hashed and signed with `owner`'s private key \(this is why `owner`'s account needs to be unlocked\).

Signature, the confirmation code's hash, the user's normalized profile link, and the session code are sent back to the client. User then confirms the transaction in MetaMask and invokes the contract's method. The contract combines input data in the same order as the server did, hashes it, and then uses the built-in function `ecrecover` to validate that the signature belongs to the `owner`. If it doesn't, the contract rejects the transaction, otherwise it adds some metadata, most importantly the current block's number, and saves it in the blockchain.

When the transaction is mined, `tx_id` is returned to the client and then via the client to the server along with the session code. Server queries memory by the session code and validates the user's eth address. Then it fetches the transaction from the blockchain by `tx_id`. It verifies that `tx.to` is equal to `owner` and `tx.from` is equal to the user's eth address. Then, using `tx.blockNumber` the server uses the contract's method to find the profile link added at that blockNumber. User should be limited to registering at most one profile link per eth block.

Then the server uses the session code to get plain text confirmation code from memory and enclose it into a predefined meaningful text, e.g.:

```text
My POA identity confirmation code is <confirmation code>
```

\(As a side note, it'd be funny if the confirmation code was a random quote from a random book.\) Then the server sends this confirmation phrase back to the client and removes the session code from memory to prevent reuse.

User must create a publicly available post where the confirmation phrase would appear alone, on a separate line \(there may be other text in this post, on other lines\).

Then the user returns to the DApp and submits the link to his/her post. Server needs to scrape this post, find a line starting with the predefined text and extract the confirmation code from it. Server then calculates SHA-3 of the confirmation code and signs it with the `owner`'s private key. Hash of the confirmation code and signature is returned to the client.

User then confirms the transaction in MetaMask, which invokes the contract's method. Contract first of all uses `ecrecover` to verify that the signature belongs to the `owner`. If it doesn't, the contract rejects the transaction, otherwise it computes the confirmation code's hash and loops through the user's profile links to find a matching one. Server must also double-check that post is on the same network that is in the profile link in the contract's data.

### Possible cheating

1. _user can generate his/her own confirmation code, compute all hashes, and submit it to the contract, and then confirm it_ This can't be done because the user doesn't know the `owner`'s private key and therefore can't compute a valid signature.
2. _user can reuse someone else's confirmation code, or his/her own confirmation code from one of the previously confirmed profile links_ This is prevented by hashing all essential pieces of data together before signing \(user's eth address, profile link, confirmation code\) and by checking the profile link for duplicates in the contract.
3. _user can submit the form, but doesn't sign the transaction_ For this reason confirmation phrase is sent to the client after the profile link is added to the blockchain and `tx_id` presented to the server.
4. _since user knows confirmation code right from the start \(cf. PoPA DApp\), he/she can avoid posting the confirmation phrase and just call the contract's method directly_ Link to the post should be presented to the server, which scrapes it, extracts the confirmation code, and then signs it with the `owner`'s private key.
5. _user can post the confirmation phrase on some other social network or website_ Server should double-check that the post is on the same network as the profile link from the contract's data. 6. _user can resubmit the same tx\_id to the server multiple times_ This is prevented by removing the session code from memory after the first postcard is sent.

