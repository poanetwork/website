---
description: Parity may need to be updated to prepare for a hard fork
---

# Parity Upgrade Guide

{% hint style="info" %}
This guide assumes you are running this playbook from the same machine you used initially deploy of your node. You should already have `python` and `ansible` installed, and the correct ssh keypair to root-access the node.
{% endhint %}

## Running the update

1\) Clone the poa-devops repository if you haven't done so before

```text
git clone https://github.com/poanetwork/poa-devops.git
cd poa-devops
```

or pull the latest changes

```text
cd poa-devops
git pull origin master
```

2\) Create `group_vars/all` file:

```text
cp group_vars/upd-parity-version.example group_vars/all
```

and change the following variables:

1. `poa_role` - role of the node on the network \(select one of these: `bootnode`, `validator`, `moc`, `explorer`\)
2. `GENESIS_BRANCH` - either `"sokol"` or `"core"` or `"dai"` or `"kovan"` depending which network you're updating

DO NOT change other options

3\) Create/edit `hosts` file and put your node's ip address \(assuming it's 192.0.2.1\) there with the following header:

```text
[upd-parity-version]
192.0.2.1
```

{% hint style="info" %}
If you're updating an existing file, make sure you remove other tags `[...]` and ips.
{% endhint %}

4\) Run the playbook \(change user: ubuntu to your user name, if necessary\):

```text
ansible-playbook -i hosts upd-parity-version.yml
```

{% hint style="warning" %}
If you get a ssh connection error, try to add option `-e 'ansible_ssh_user=ubuntu'` and/or `--user="ubuntu"` to the command line above, substituting `ubuntu` with correct ssh username, which is usually either `ubuntu` or `root` or `poa` or `centos` depending on your setup. You may also need to specify exact path to your ssh private key with `--key-file=/path/to/private.key` cli option.

If you are installing an update to the localhost machine, use `-c local` instead of specifying the private key.
{% endhint %}

## Verifying the update

{% hint style="success" %}
Playbook run should complete without errors.
{% endhint %}

1\) Open network statistic webpage:

* for sokol test network: [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network)
* for core main network: [https://core-netstat.poa.network](https://core-netstat.poa.network)
* for dai network: [https://dai-netstat.poa.network](https://dai-netstat.poa.network)
* for kovan network: [https://kovan-netstat.poa.network](https://kovan-netstat.poa.network)

check that your node is "green" and is catching new blocks. It may take 5-6 minutes to fully start and reconnect.

2\) Connect to the node

```text
ssh root@192.0.2.1
```

and check parity version \(replace `bootnode` with correct role name ,e.g. `validator`\):

```text
/home/bootnode/parity --version
```

sample output \(version number may be different\):

```text
Parity Ethereum
  version Parity-Ethereum/v2.4.6-stable-94164e1-20190514/x86_64-linux-gnu/rustc1.34.1
Copyright 2015-2018 Parity Technologies (UK) Ltd.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

By Wood/Paronyan/Kotewicz/Drwięga/Volf
   Habermeier/Czaban/Greeff/Gotchac/Redmann
```

3\) During the next day check the status of your node on network status webpage and associated functions \(e.g. for validators - are block rewards still being sent from your mining key to your payout key?\).

## Rollback to the previous version \(in case of problems\)

{% hint style="warning" %}
**I**f you get any errors please consult the POA Team first, most likely it is a minor issue and you don't need to rollback.
{% endhint %}

1\) Connect to the node:

```text
ssh root@192.0.2.1
```

2\) Switch to your home folder \(replace `bootnode` with correct role name\):

```text
cd /home/bootnode
```

3\) Stop services:

```text
systemctl stop poa-netstats
systemctl stop poa-parity
```

4\) Locate the backup folder:

```text
ls backups-version
```

it contains folders labeled by the time backup was created in format`<year><month><day>T<hour><minute><second>`, e.g.

```text
# ls backups-version
20190311T200132 20190614T214517
```

copy the version number that corresponds to this day. In the following examples we assume that it's `20180209T214517`.

5\) Make sure you have your mining key data \(keyfile, password, address\) available to you.

6\) Remove files from the new version:

```text
rm -rf parity_data
rm parity
rm node.toml
```

7\) Restore previous versions of these files from backup \(**note dots `.` at the end of each line here, they are important**\):

```text
cp -a backups-version/20190614T214517/parity .
cp -a backups-version/20190614T214517/parity_data .
cp -a backups-version/20180614T214517/node.toml .
```

8\) Check parity version \(must be previous one\):

```text
./parity --version
```

sample output \(version number may be different\):

```text
Parity Ethereum
  version Parity-Ethereum/v2.3.2-beta-678138f-20190203/x86_64-linux-gnu/rustc1.31.1
Copyright 2015-2018 Parity Technologies (UK) Ltd.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

By Wood/Paronyan/Kotewicz/Drwięga/Volf
   Habermeier/Czaban/Greeff/Gotchac/Redmann
```

9\) Restart services

```text
systemctl restart poa-parity
systemctl restart poa-netstats
```

10\) Open network statistic webpage:

* for sokol test network: [https://sokol-netstat.poa.network](https://sokol-netstat.poa.network/)
* for core main network: [https://core-netstat.poa.network](https://core-netstat.poa.network/)
* for dai network: [https://dai-netstat.poa.network](https://dai-netstat.poa.network/)

Check that your node is "green" and is catching new blocks. It may take 2-3 minutes to fully start and reconnect.

