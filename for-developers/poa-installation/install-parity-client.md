# Install OpenEthereum Client

## Requirements

* [OpenEthereum client](https://github.com/openethereum/openethereum/releases)
* [Modifications to spec.json file](https://github.com/poanetwork/poa-chain-spec/) \(in POA GitHub repo\)

## 1\) Download OpenEthereum

You can build from [source](https://github.com/openethereum/openethereum) or download binary release, see the official [OpenEthereum Releases Page](https://github.com/openethereum/openethereum/releases). Please use  `OpenEthereum` versions \(2.7.2 - 3.0.1\).

After downloading, you need to perform the command `chmod +x openethereum` to be able to run the binary.

## 2\) Once OpenEthereum is Installed, Connect and Sync with POA

### **POA Core**

```text
openethereum --chain poacore --no-warp
```

### Sokol

```text
openethereum --chain poasokol --no-warp
```

#### Optional

`--no-warp` flag is optional: [more information.](https://openethereum.github.io/wiki/Getting-Synced)

### Setting specific bootnodes

_If you would like to limit or choose specific bootnodes, you can obtain the bootnodes.txt file from POA github. E_nter all supplied enodes for the desired network separated by a comma, no space  
  
**POA Core**

```bash
git clone -b core https://github.com/poanetwork/poa-chain-spec.git
```

```text
openethereum --chain poacore --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT
```

**POA Sokol**

```bash
git clone -b sokol https://github.com/poanetwork/poa-chain-spec.git
```

```text
openethereum --chain poasokol --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT
```

## 3\) Connect to your Node

You can use [Ethereum's JSON-RPC](https://openethereum.github.io/JSONRPC) or a JavaScript console.

