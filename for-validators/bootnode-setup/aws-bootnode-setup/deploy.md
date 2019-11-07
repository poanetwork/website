# Deploy

#### Create instance

1. with all options configured, you first need to create an instance: \(you should still be in: ~/deployment-playbooks\)

   ```text
   ansible-playbook bootnode.yml
   ```

   this script will ask you for your SSH key passphrase unless you didn't set a passphrase or you entered it recently.  

2. after this process is complete, examine script's output and write down IP \(e.g. `192.0.2.1`\) address and AWS InstanceID \(e.g. `i-0123456789abcdef0`\) for later use. If you chose to use elastic IP, write down node's final IP address. 
3. create file `hosts` with the server's ip address \(e.g. 192.0.2.1\):

   ```text
   [bootnode]
   192.0.2.1
   ```

4. run ansible playbook

   ```text
   ansible-playbook -i hosts site.yml
   ```

5. open `NETSTATS_SERVER` url in the browser and check that the node named `NODE_FULLNAME` appeared in the list. 
6. login to the node and get enode from parity logs:

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

after that refresh `NETSTATS_SERVER` url and check again your node's block number. If your node is still not active or missing `enode`, log in to root account and reboot the OS.

```text
su 
shutdown -r now
```

