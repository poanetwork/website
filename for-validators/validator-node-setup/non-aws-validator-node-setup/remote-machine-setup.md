# Remote Machine Setup

Log into your Cloud Dashboard and deploy a new node with a minimum of 1 CPU, 1GB \(1024Mb\) Memory & at least 4GB Hard Drive Capacity \(This may need to be upgraded in future\). This guide will be using `ubuntu` as the username, use the default or replace with your `sudo` username.

* If prompted to create new user during deployment, do so and skip the section about adding new user.
* If prompted to add SSH Key for your new user, follow the steps below to generate your SSH Key and follow directions how to add to deployment.

**Generating SSH Key**

1. On your local control machine, open a terminal and generate your SSH key. It is recommended to use a different SSH Key for each POA network, key for `core` & key for `sokol`. We can set a parameter in ansible inventory script to use the specific key.

   ```text
    ssh-keygen -t rsa -b 4096 -C "node-label"
   ```

   Enter a **STRONG** password \(write it down\) and save the key as something memorable, enter complete path to key to save as custom name, replacing `user` with your current local user. e.g. below

   ```text
    /home/ubuntu/.ssh/id_poa-core
    /home/ubuntu/.ssh/id_poa-sokol
   ```

* This will save 2 files, .pub will be your public key and the other is your private key. Private SSH key stays on your local machine and Public key gets copied to remote machines you want access to.

**Add User with Sudo Privileges**

1\) SSH into Remote Node using the root password provided by cloud service \(either by web portal or email\) or using the SSH key supplied during deployment. If you already have `sudo` user, replace `root` with your user and skip the next two steps.  
_**Azure users will not have access to their root account by default, use your sudo user and skip to next section after connecting.**_

```text
 ssh root@192.0.2.1
```

2\) Logged in as `root` add user and grant sudo privileges. It is recommended to use default user `ubuntu`.

```text
 adduser ubuntu
```

* Enter a **STRONG** password to protect the user and you can leave the next 5 fields blank. Confirm the information is correct. We will be using a parameter to ask `sudo` pass during ansible deployment.

3\) Grant user `ubuntu` sudo privileges

```text
 usermod -aG sudo ubuntu
```

3\) Copy authorized keys from `root` to `ubuntu` user
```text
su ubuntu
mkdir -p ~/.ssh
touch ~/.ssh/authorized_keys
ctrl+d
cat ~/.ssh/authorized_keys >> /home/ubuntu/.ssh/authorized_keys
```
Your Non-AWS node is now ready for configuration using ansible-playbook provided by POA. 

{% hint style="success" %}
Continue to [Node Configuration with Deployment Playbook](configure-node-using-deployment-playbook.md)
{% endhint %}



