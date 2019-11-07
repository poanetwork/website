# Download and Configure Playbook

You may need to add your github info, if you haven't already. This may require the creation of a new "Personal Access Token".

1. clone repository with ansible playbooks and checkout branch with the network name you want to join \(e.g. `core` for mainnet and `sokol` for testnet\)

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

  2. prepare files with ssh keys

```text
cat ~/.ssh/id_rsa.pub > files/admins.pub
cp files/admins.pub files/ssh_bootnode.pub
```

   3. create file with configuration settings:

```text
cat group_vars/all.network group_vars/bootnode.example > group_vars/all
```

    4. to choose subnet run the following command

```text
aws ec2 describe-subnets
```

select any subnet with "State": "available" and non-zero "AvailableIpAddressCount". You need to copy/save "SubnetId" of this subnet for later use.

   5. open `group_vars/all` and edit the following configuration options:

```text
nano group_vars/all
```

Make the following edits:

* `access_key` - your AWS "Access Key ID"
* `secret_key` - your AWS "Secret Access Key"
* `awskeypair_name` - name of ssh keypair you uploaded on AWS \(by default `id_rsa`\)
* `vpc_subnet_id` - insert "SubnetId" that you chose. The next line should look like this:

  ```text
  vpc_subnet_id: "subnet-..."
  ```

* `NODE_FULLNAME` - enter your node's name \(this will be visible to other members of the network\). Please consult with Master of Ceremony about naming convention for bootnodes.
* `NODE_ADMIN_EMAIL` - enter your public email \(this will be visible to other members of the network\)
* `NETSTATS_SERVER` - this should be a url provided to you by the Master of Ceremony
* `NETSTATS_SECRET` - this should be a secret code provided to you by the Master of Ceremony
* `allow_bootnode_ssh` - leave this value set to `true`
* `allow_bootnode_p2p` - set this value to `true`
* `allow_bootnode_rpc` - set this value to `false`
* `associate_bootnode_elastic_ip` - set this to `false`, unless you want to configure AWS Elastic IP for your node

   6. examine values in `image` and `region` properties. If your AWS region doesn't match the one in `region` you need to replace `region` with the correct one and select image from this list [https://cloud-images.ubuntu.com/locator/ec2/](https://cloud-images.ubuntu.com/locator/ec2/)

Open this page, scroll down, choose your region from the first \("Zone"\) dropdown list, choose `xenial` from the second \("Name"\) dropdown list and `hvm:ebs-ssd` from the fifth \("Instance type"\). This should limit you to a single option, copy value from "AMI-ID" column and paste it in `image` property.

  7. you may also choose a different value for the `bootnode_instance_type`. For `region: "us-east-2"` we recommend using `m4.xlarge`. Confirm your option of the types of instances available in your region, via: [https://aws.amazon.com/ec2/pricing/on-demand/](https://aws.amazon.com/ec2/pricing/on-demand/)

{% hint style="success" %}
Proceed to [Deploy](deploy.md) your instance
{% endhint %}

