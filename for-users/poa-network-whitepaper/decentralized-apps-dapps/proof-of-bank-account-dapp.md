# Proof of Bank Account DApp

![Click on image to enlarge](../../../.gitbook/assets/poba.png)

In contrast to other identity DApps, PoBA is \(from the contract's point of view\) a one-step verification process.

DApp client and server are integrated with bank accounting API service \(plaid.com\).

Client side uses the service's widget \(Plaid Link\) to authenticate the user, and as a result of successful authentication, access\_token is returned from Plaid to the client. User then fills out a form with his/her bank account number and submits it to the server alongside Plaid's access token.

Server consists of a web app and a parity node connected to the blockchain. The node is run under the ethereum account that was used to deploy the PoP contract \(contract's `owner`\). This account needs to be unlocked.

Server validates and normalizes the user's account number by removing trailing spaces. Then the server fetches the bank account numbers from Plaid using access\_token. It checks that the account number submitted by the user is present in the list returned by Plaid.

Server then combines `user's eth address + bank's name + account number` into a single string and hashes it with SHA-3 function. The hash is then signed with `owner`'s private key \(this is why `owner` account needs to be unlocked\).

Signature, normalized account number, and bank name are returned to the client. User then signs the transaction in MetaMask and invokes the contract's method.

Contract checks that the account number for this bank for this eth address doesn't already exist. If it does, the contract rejects the transaction. Otherwise, it combines parameters in the same order as the server did and computes `sha3` hash of them. Then it uses the built-in `ecrecover` function to validate that the signature belongs to the `owner`. If it doesn't, the contract rejects the transaction, otherwise, it saves the information to the blockchain.

### Possible cheating

1. _user can generate his/her own confirmation code, compute all hashes, and submit it to the contract, and then confirm it_ This can't be done because the user doesn't know the `owner`'s private key and hence can't compute a valid signature.
2. _user can use someone else's access\_token returned by Plaid and thus verify the account he/she has no real access to_ This is equivalent to either hacking someone else's computer or the account's owner deliberately providing the user with his/her access\_token. Since all communications with Plaid are via HTTPS protocol, there is no way for the user to intercept access\_token sent to someone else.

