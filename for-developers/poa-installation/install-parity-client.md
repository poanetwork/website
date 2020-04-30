# Install OpenEthereum Client

## Requirements

* [OpenEthereum client](https://github.com/openethereum/openethereum/releases)
* [Modifications to spec.json file](https://github.com/poanetwork/poa-chain-spec/) \(in POA GitHub repo\)

## 1\) Download OpenEthereum

You can build from [source](https://github.com/openethereum/openethereum) or download binary release, see the official [OpenEthereum Releases Page](https://github.com/openethereum/openethereum/releases). Please use a stable `OpenEthereum` version \(2.7.2 or later\).

After downloading, you need to perform the command `chmod +x openethereum` to be able to run the binary.

## 2\) Connect and Sync with POA Network

### Connecting Linux/MacOS to POA Network on OpenEthereum

Obtain the [spec.json](https://github.com/poanetwork/poa-chain-spec/blob/core/spec.json) and [bootnodes.txt](https://github.com/poanetwork/poa-chain-spec/blob/core/bootnodes.txt) files from POA Github.

{% hint style="info" %}
For POA Sokol Testnet, select the appropriate **branch** on Github.
{% endhint %}

**1\) Clone the appropriate Github Repo**

For Core\(live\) network

```text
git clone -b core https://github.com/poanetwork/poa-chain-spec.git
```

For Sokol\(test\) network

```text
git clone -b sokol https://github.com/poanetwork/poa-chain-spec.git
```

2\) In terminal run

```text
./openethereum --chain /path/to/spec.json --reserved-peers /path/to/bootnodes.txt
```

If you would like to limit or choose specific bootnodes, run

```text
./openethereum --chain /path/to/spec.json --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT
```

Enter all the supplied enodes for the desired network separated by a comma, no space. 

### Connecting a Windows machine to POA Network on OpenEthereum

Obtain [spec.json](https://github.com/poanetwork/poa-chain-spec/blob/core/spec.json) and [bootnodes.txt](https://github.com/poanetwork/poa-chain-spec/blob/core/bootnodes.txt) files from POA Github.

{% hint style="info" %}
For POA Sokol Testnet, select the appropriate **branch** on Github.
{% endhint %}

**1\) Use Git Bash with the following commands** 

For Core\(live\) network

```text
git clone -b core https://github.com/poanetwork/poa-chain-spec.git
```

For Sokol\(test\) network

```text
git clone -b sokol https://github.com/poanetwork/poa-chain-spec.git
```

2\) Open Windows Command Prompt CMD or Windows Powershell and navigate to OpenEthereum executive file.

```text
openethereum --chain c:\path\to\spec.json --reserved-peers c:\path\to\bootnodes.txt
```

If you would like to limit or choose specific bootnodes, run

```text
openethereum --chain c:\path\to\spec.json --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT
```

Enter all the supplied enodes for the desired network separated by a comma, no space. 

## 3\) Connect to your Node

You can use Ethereum's JSON-RPC or a JavaScript console: [https://github.com/openethereum/wiki/blob/master/Basic-Usage.md](https://github.com/openethereum/wiki/blob/master/Basic-Usage.md)

