# Configure Node using Deployment Playbook

To run playbook you will need a user on the server with `sudo` privileges and who can be logged in via SSH public key. By default it is assumed that this user is called `ubuntu`. If you already have a user with different name who satisfies these requirements, at the top of `site.yml` in `-hosts: all` section change line `user: ubuntu` to the `sudo` user you have

```
---
- hosts: all
  user: ubuntu
  become: True
...
```

{% hint style="info" %}
Playbook will additionally create a new unprivileged user named `validator` and add your ssh public key to `root` account.
{% endhint %}

_1)_ Clone repository with ansible playbooks and checkout branch with the network name you want to join (e.g. `core` for mainnet and `sokol` for testnet)

```
git clone https://github.com/poanetwork/deployment-playbooks.git
cd deployment-playbooks
# for core mainnet
git checkout core
# OR for sokol testnet
git checkout sokol
# check that you ended up on a correct branch (look where the `*` is)
git branch
```

2\) two files with ssh public key need to be created for ansible playbook to configure node correctly, use the path to your desired key.

```
cat ~/.ssh/id_poa-core.pub > files/admins.pub
cp files/admins.pub files/ssh_validator.pub
```

3\) create configuration file

```
cat group_vars/all.network group_vars/validator.example > group_vars/all
```

4\) edit the `group_vars/all` file and comment out parameters corresponding to aws:

```
#access_key
#secret_key
#awskeypair_name
#vpc_subnet_id
```

5\) set values given to you by Master of Ceremony for the following parameters in `group_vars/all`:

* `NODE_FULLNAME` - your real name (will be visible to other members of the network)
* `NODE_ADMIN_EMAIL` - your public email address (will be visible to other members of the network)
* `MINING_KEYFILE` - insert content of your mining keystore json file. Resulting value should be enclosed in single quotes and look similar to this: `MINING_KEYFILE: '{"address":"..."}'`
* `MINING_ADDRESS` - insert your mining key address, e.g. `MINING_ADDRESS: "0x..."`
* `MINING_KEYPASS` - insert your mining key password

8\) set values given to you by Master of Ceremony for the following parameters in `group_vars/all`:

* `NETSTATS_SERVER`
* `NETSTATS_SECRET`

9\) set the following options as follows in `group_vars/all`:

```
allow_validator_ssh: true
allow_validator_p2p: true
associate_validator_elastic_ip: false
```

{% hint style="warning" %}
Double check that `allow_validator_ssh` is `true` otherwise you won't be able to connect to the node.
{% endhint %}

_10)_ create file `hosts` with the server's ip address (e.g. 192.0.2.1):

```
[validator]
192.0.2.1
```

11\) run ansible playbook, replace the `--key-file` path with your desired SSH key

```
ansible-playbook -i hosts site.yml -K --key-file "~/.ssh/id_poa-core"
```

12\)open `NETSTATS_SERVER` url in the browser and check that the node named `NODE_FULLNAME` appeared in the list

13\) [Setup Metadata in Validators DApp](../../validator-dapps/validators-metadata-dapp.md#for-validators-update-metadata)

### **Sokol Only Instruction:**

{% hint style="info" %}
Skip this step if you are deploying your node to CORE network. You should not make your `enode` public as it will make your validator node an easy target for denial of service attacks.
{% endhint %}

If you are deploying on a testnet (sokol), follow the steps below: login to the node and get enode from parity logs:\


_Without access to `root` you can use `sudo` user instead, append `sudo` in front of commands after connecting to remote machine_

```
ssh root@192.0.2.1
grep enode /home/validator/logs/parity.log
```

copy `enode` uri and send it to Master of Ceremony. If this line is not found, restart parity

```
systemctl restart poa-parity
```

and try again. If `enode` uri is still not found, use the commands below to restart all services.

_NOTE_ if after parity restart you notice that on `NETSTATS_SERVER` url your node starts to fall behind other nodes (block number is less than on other nodes), try to restart statistics service (assuming you are connected as `root`):

```
su validator
pm2 restart all
```

after that refresh `NETSTATS_SERVER` url and check your node's block number. If your node is still not active or missing `enode`, log in to root account and reboot.\
_Without access to `root` you can use `sudo` user instead, append `sudo` in front of commands after connecting to remote machine_

```
su
shutdown -r now
```
