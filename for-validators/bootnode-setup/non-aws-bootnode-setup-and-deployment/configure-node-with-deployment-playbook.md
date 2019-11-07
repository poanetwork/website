# Configure node with Deployment Playbook

To run playbook you will need a user on the server with `sudo` privileges and who can be logged in via SSH public key. By default it is assumed that this user is called `ubuntu`. If you already have a user with different name who satisfies these requirements, at the top of `site.yml` in `-hosts: all` section change line `user: ubuntu` to the `sudo` user you have

```text
---
- hosts: all
  user: ubuntu
  become: True
...
```

{% hint style="info" %}
Playbook will additionally create a new unprivileged user named `bootnode` and add your ssh public key to `root` account.
{% endhint %}

1\) Clone repository with ansible playbooks and checkout branch with the network name you want to join \(e.g. `core` for mainnet and `sokol` for testnet\)

```text
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

```text
cat ~/.ssh/id_poa-core.pub > files/admins.pub
cp files/admins.pub files/ssh_bootnode.pub
```

3\) create configuration file

```text
cat group_vars/all.network group_vars/bootnode.example > group_vars/all
```

4\) edit the `group_vars/all` file and comment out parameters corresponding to aws:

```text
#access_key
#secret_key
#awskeypair_name
#vpc_subnet_id
```

5\) set values given to you by Master of Ceremony for the following parameters in `group_vars/all`:

* `NODE_FULLNAME`
* `NODE_ADMIN_EMAIL`
* `NETSTATS_SERVER`
* `NETSTATS_SECRET`

6\)  set the following options as follows:

```text
allow_bootnode_ssh: true
allow_bootnode_p2p: true
allow_bootnode_rpc: false
associate_bootnode_elastic_ip: false
```

{% hint style="warning" %}
Double check that `allow_bootnode_ssh` is `true` otherwise you won't be able to connect to the node.
{% endhint %}

7\) create file `hosts` with the server's ip address \(e.g. 192.0.2.1\):

```text
[bootnode]
192.0.2.1
```

8\) run ansible playbook, replace the `--key-file` path with your desired SSH key

```text
ansible-playbook -i hosts site.yml -K --key-file "~/.ssh/id_poa-core"
```

9\) open `NETSTATS_SERVER` url in the browser and check that the node named `NODE_FULLNAME` appeared in the list

10\) login to the node and get enode from parity logs:  
_Without access to `root` you can use `sudo` user instead, append `sudo` in front of commands after connecting to remote machine_

```text
ssh root@192.0.2.1
grep enode /home/bootnode/logs/parity.log
```

copy `enode` uri and send it to Master of Ceremony. If this line is not found, restart parity

```text
systemctl restart poa-parity
```

and try again. If `enode` uri is still not found, use the commands below to restart all services.

{% hint style="info" %}
if after parity restart you notice that on `NETSTATS_SERVER` url your node starts to fall behind other nodes \(block number is less than on other nodes\), try to restart statistics service \(assuming you are connected as `root`\):
{% endhint %}

```text
su bootnode
pm2 restart all
```

after that refresh `NETSTATS_SERVER` url and check your node's block number. If your node is still not active or missing `enode`, log in to root account and reboot.  


{% hint style="info" %}
Without access to `root` you can use `sudo` user instead, append `sudo` in front of commands after connecting to remote machine
{% endhint %}

```text
su
shutdown -r now
```

