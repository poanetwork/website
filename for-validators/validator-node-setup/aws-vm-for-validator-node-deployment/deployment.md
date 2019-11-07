# Deployment

## Create instance

1\) with all options configured, you first need to create an instance: \(you should still be in: ~/deployment-playbooks\)

```text
ansible-playbook validator.yml
```

Running this script creates and powers up your remote AWS instance. this script will also ask you for your SSH key passphrase unless you didn't set a passphrase or you entered it recently.

2\) after this process is complete, examine script's output and write down IP \(e.g. `192.0.2.1`\) address and AWS InstanceID \(e.g. `i-0123456789abcdef0`\) for later use. If you chose to use elastic IP, write down node's final IP address.

## Configure instance

1\) create file `hosts` with the following content \(assuming IP address is `192.0.2.1`, gathered from previous step\)

```text
touch hosts
echo [validator] > hosts
echo 192.0.2.1 >> hosts

NOTE:  Feel free to edit the hosts file directly with any text editor (vi, pico, etc.) - file must contain at minimum:
[validator]
192.0.2.1
```

2\) run this script to configure your remote node instance:

```text
ansible-playbook -i hosts site.yml
```

if you get an error that host cannot be reached over SSH, please wait a minute and start again. This error may appear because AWS instance is rebooted after creation, and this may take some time to complete.

3\) open the url for `NETSTAT_SERVER` and check that your node has appeared in the list

## Set Metadata‌ in DApp

Follow the guide on how to [Update Validator MetaData.](evernote-html-snippet:///@poa/s/poa/~/drafts/-Lt65LU4zQf0k_iW4w-G/for-validators/validator-dapps/validators-metadata-dapp#for-validators-update-metadata)

## Obtaining enode uri for Master of Ceremony

{% hint style="warning" %}
**NOTE** skip this step if you are deploying your node to CORE network. You should not make your `enode` public as it will make your validator node an easy target for denial of service attacks
{% endhint %}

If you are deploying on a testnet \(sokol\), follow the steps below: 

1\) Login to the node and get enode from parity logs:

```text
ssh root@192.0.2.1 OR, if root SSH access is not enabled:
ssh -l ubuntu 192.0.2.1  #NOTE: replace 'ubuntu' with a different remote node user if you are not using the recommended example user.  Once logged in, become Super User by executing:

sudo su    #NOTE:  enter the 'ubuntu' user password, or other user password if you have created a different user.  You should now be Super User, with all of the powers and identity of the 'root' user.  Be careful!

grep enode /home/validator/logs/parity.log
```

2\) copy `enode` uri and send it to Master of Ceremony. If this line is not found, restart parity

```text
systemctl restart poa-parity
```

and try again. If `enode` uri is still not found, use the commands below to restart all services.

{% hint style="info" %}
If after parity restart you notice that on `NETSTATS_SERVER` url your node starts to fall behind other nodes \(block number is less than on other nodes\) and has not caught up after a few minutes, _try the following:_ 
{% endhint %}

1\) try to restart statistics service \(assuming you are connected as `root`\):

```text
su validator
pm2 restart all
```

after that, refresh the `NETSTATS_SERVER` url in your browser and check your node's block number again. If your node is still not active or missing `enode` entry

2\) log in to root account and reboot the OS. 

PLEASE WAIT at least five minutes for your node to "catch up" before rebooting your remote server, and do so only as a final resort.

```text
su
shutdown -hr now
```

## Configure access to your node

Later, you may wish to change access options for your node. For example, initially you might have disabled access over ssh but now want to re-enable it. These options are set by parameters in the file group\_vars/all:

* `allow_validator_ssh` - `true`/`false` - allow/deny access over ssh
* `allow_validator_p2p` - `true`/`false` - allow/deny peer-discovery

When you make changes, rerun the playbook:

```text
ansible-playbook -i hosts site.yml
```

{% hint style="info" %}
tThis script applies simultaneously to all your instances with security group named `validator-security` and technically any other servers in your 'hosts' file. This note is relevant only if you have several validator node or other instances running.
{% endhint %}

## Remove Instance

**If you want to remove your AWS instance:**

a. do it via AWS GUI: open AWS management console [https://console.aws.amazon.com/ec2/v2/home\#Instances](https://console.aws.amazon.com/ec2/v2/home#Instances) check the instance you want to remove, click Actions &gt; Instance State &gt; Terminate.

b. do it via aws cli: get AWS Instance ID \(the one you saved previously, or you can look it up in AWS management console\) and run

```text
aws ec2 terminate-instances --instance-ids i-0123456789abcdef0
```

\(replace `i-0123456789abcdef0` with your actual AWS InstanceID\).

{% hint style="danger" %}
This operation is irreversible! If you want to redeploy, you will have to create a new instance from scratch.
{% endhint %}

