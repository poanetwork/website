# Install Parity Client

## Requirements

* [Parity Ethereum client](https://github.com/paritytech/parity-ethereum/releases)
* [Modifications to spec.json file](https://github.com/poanetwork/poa-chain-spec/) \(in POA Github repo\)

## 1\) Install Parity

### Ubuntu/Debian & MacOS with Homebrew one-line Binary Installation

Faster than building from source, but no cutting edge features.

If you would like to build from [source](https://github.com/paritytech/parity) or download binary release, see the official [Parity Releases Page](https://github.com/paritytech/parity/releases). Please use a stable `Parity` version \(1.11.8 or later\).

1\) Open a bash Terminal and enter the command below, if the client needs an update simply run the command a second time.

```text
bash <(curl https://get.parity.io -kL)
```

This will install and configure the Parity client for you. On Ubuntu, this script will also offer to install the Netstats client and connect it to ethstats.net. If you plan on using `Parity` for POA only, there is no need to install the extra software. 

### **Installing from the Linux distro Snap Service**

```text
sudo snap install parity --edge
```

### Installing Parity on Windows

Parity on Windows can either be installed as a System Service or executed from a folder. Choose the desired executable file from  [Parity's Releases Page](https://github.com/paritytech/parity/releases). To connect to POA Network using `Parity` on Windows, please follow the appropriate section below.

## 2\) Connect and Sync with POA Network

### Connecting Linux/MacOS to POA Network on Parity

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
parity --chain /path/to/spec.json --reserved-peers /path/to/bootnodes.txt ui
```

If you would like to limit or choose specific bootnodes, run

```text
parity --chain /path/to/spec.json --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT ui
```

Enter all the supplied enodes for the desired network separated by a comma, no space. 

### Connecting a Windows machine to POA Network on Parity

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

2\) Open Windows Command Prompt CMD or Windows Powershell and navigate to `Parity` executive file.

```text
parity --chain c:\path\to\spec.json --reserved-peers c:\path\to\bootnodes.txt ui
```

If you would like to limit or choose specific bootnodes, run

```text
parity --chain c:\path\to\spec.json --bootnodes enode://ENODE@IP:PORT,enode://ENODE@IP:PORT ui
```

Enter all the supplied enodes for the desired network separated by a comma, no space. 

## 3\) Connect to your Node

You can use Ethereum's JSON-RPC or a JavaScript console: [https://wiki.parity.io/Basic-Usage](https://wiki.parity.io/Basic-Usage)

Parity's UI is deprecated, but information on the site provides alternatives to a local Parity Ethereum node: [https://wiki.parity.io/Parity-Wallet](https://wiki.parity.io/Parity-Wallet)

