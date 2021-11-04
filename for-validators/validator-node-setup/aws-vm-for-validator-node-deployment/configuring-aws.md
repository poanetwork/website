# Configuring AWS

1. Register (if you haven't already) and login to the AWS management console: [https://aws.amazon.com/console/](https://aws.amazon.com/console/)\

2. to create credentials for cli, open IAM home [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home), select "Users" on the left hand side navigation bar and then click "Add user". Pick a username, and check "Programmatic access" for "Access type". NOTE: For clarity we recommend using identical usernames on your Ansible Control Station and your remote node. For example, one can create a user named "ubuntu" on both your Ansible Control Station and your remote note.\

3. Click "Next: Permissions" - you can choose any of the available options, and "Attach existing policies directly" is the simplest one. In the list of policy types, search for and then check "AmazonEC2FullAccess". Click "Next:Review". Review your account and click "Create user" to proceed.\

4. **it is very important that you copy "Access Key ID" and "Secret Access Key" without leaving this page,** because there is no other way to retrieve "Secret Access Key" later and you will have to start again and create another user. After copying this important information, select "Close".\

5.  after you've copied and saved your AWS secret keys, the next step is to upload your SSH public key. In the top left corner of the page select "Services -> EC2". On the left sidebar select "Network & Security" -> "Key Pairs". Click "Import Key Pair". Give a name to this keypair, otherwise base name of the file will be used (by default `id_rsa`). Browse your Ansible Control Station file system for the public key, or copy/paste:

    ```
    pbcopy < ~/.ssh/id_rsa.pub
    ```

    This will copy your public key into your clipboard and can then be pasted.\

6.  configure aws cli:

    ```
    aws configure
    ```

    provide your credentials (Access Key ID and Secret Access Key) from earlier. Choose a region for your account (e.g. `us-east-2`) and output format (`json` is recommended).\

7.  check that keypair was correctly imported:

    ```
    aws ec2 describe-key-pairs
    ```

    you should see your keypair name in the list.

{% hint style="success" %}
Continue to [Download and Configure Playbook](download-and-configure-playbook.md)
{% endhint %}
