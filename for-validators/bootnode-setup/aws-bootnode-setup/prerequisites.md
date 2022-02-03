# Prerequisites

* git
* python & pip:&#x20;
  * python 2 version >= 2.6.5 or python 3 version >= 3.3&#x20;
* ansible
* SSH keys
* aws cli

## 1. git

1.  check that you have git installed

    ```
    git --version
    ```

    if not - install it following instructions [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## 2. python & pip

1.  check that you have python 2 version >= 2.6.5 or python 3 version >= 3.3 installed

    ```
    python --version
    ```

    if not - install it choosing apropriate binary from [here](https://www.python.org/downloads/)\

2.  check if you have `pip` python package manager install

    ```
    pip --version
    ```

    if not - install it following instructions from [here](https://pip.pypa.io/en/stable/installing/). Basically, you need to download this script and save it on your computer [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py) then run

    ```
    python get-pip.py
    ```

## 3. ansible

1.  follow [this guide](http://docs.ansible.com/ansible/latest/intro\_installation.html) to install ansible. For example, you can use `pip` to do it:

    ```
    sudo pip install ansible
    ```
2.  use `pip` to install the following packages:

    ```
    sudo pip install boto
    sudo pip install boto3
    ```

## 4. SSH keys

1. check if you already have a keypair:

```
ls -la ~/.ssh
```

{% hint style="info" %}
If you already have key pair, you can skip this section.
{% endhint %}

**2.** generate ssh key-pair

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

insert your email address there and a strong password. By default, keys will be saved to `~/.ssh/` and named `id_rsa` with your public key being `~/.ssh/id_rsa.pub`.

## 5. aws cli

1.  check if you have aws cli installed

    ```
    aws --version
    ```

    if not - install it following [these instructions](http://docs.aws.amazon.com/cli/latest/userguide/installing.html). The simplest way is to use `pip`:

    ```
    pip install awscli --upgrade --user
    ```

    Mac systems with homebrew installed:

    ```
    brew install awscli
    ```

{% hint style="success" %}
Proceed to [Configure AWS](configure-aws.md)
{% endhint %}
