# Spinning up a Block Producer Node on Ubuntu

## Table of contents

* [Introduction](#introduction)
* [System requirements](#reqs)
* [Overview](#overview)
* [Step-by-step](#step)
* [Troubleshooting and maintenance](#troubleshoot)

## Introduction <a name="introduction"></a>

This document will guide you through spinning up a Block Producer Node on the U°OS testnet.

As this is a testnet, here's a couple of things you need to know beforehand:

* The U°OS developers are currently registering Block Producers manually. You will need to contact the U°OS developers on Telegram with your preferred account name and public keys.
* Your account name generated when signing up at [https://u.community/](https://u.community/) won't work for the U°OS Block Producer registration. You will need to come up with a different one and provide it to us.

For this guide, we are using a fresh Ubuntu 16.04 (xenial) running in Singapore.

## System requirements <a name="reqs"></a>

Supported operating systems:

* Mac OS
* Ubuntu
* Debian
* Fedora

RAM:

* 8 GB

## Overview of the process <a name="overview"></a>

1. Install Boost C++ libraries
2. Time sync the system
3. Clone the U°OS repository
4. Update submodules
5. Build the U°OS software. Note that this will run for over an hour, so plan accordingly.
6. Install the node from the U°OS software
7. Generate three key pairs using the U°OS software
8. Contact the U°OS developers with your preferred account name and public keys
9. Create and modify `config.ini`
10. Download a pre-created `genesis.json` file
11. Start your node
12. Create a wallet and import both your Active and Block Producer private keys
13. Register as a Block Producer


## Step-by-step <a name="step"></a>

### 1. Install the Boost C++ libraries

Install `libboost-all-dev`:

```
apt -y install libboost-all-dev
```

### 2. Time sync the system

Sync the time to where your node is actually located. Check DigitalOcean: [How To Set Up Time Synchronization on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-time-synchronization-on-ubuntu-16-04).

Since we are running this node in Singapore, we are issuing the following command:

```
sudo timedatectl set-timezone Asia/Singapore
```

### 3. Clone the U°OS repository

Create a working directory for the U°OS software:

```
mkdir uosdata
```

Change the directory to `/uosdata/`:

```
cd uosdata
```

Clone the U°OS repository:

```
git clone https://github.com/UOSnetwork/uos
```

### 4. Update the submodules

Change the directory to `/uos/`:

```
cd uos
```

Update the submodules:
```
git submodule update --init --recursive
```

### 5. Build the U°OS software

Build the U°OS software with the following command:

```
scripts/eosio_build.sh -s UOS
```

Note that this will run for over an hour, so plan accordingly.

### 6. Install the node

Install the node from the U°OS software:

```
sudo scripts/eosio_install.sh
```

Verify the version of the node:

```
nodeos --version
```

It will give you something similar to:

```
v.1.4.3
```

### 7. Generate three key pairs

You will need to generate three key pairs that you will use to manage your account:

* **Owner key pair**: Use this key pair to manage the ownership of your account; use the owner key to recover the active or producer permissions if they get compromised.
* **Active key pair**: Use this key pair to transfer funds and vote.
* **Producer key pair**: Use this key pair to manage your Block Producer account.

Generate the key pairs:

```
cleos create key --to-console
```

The command will output a key pair once on each run. Run it three times to generate three key pairs.

Label each key pair as **Owner**, **Active**, **Producer**. Labeling here just means putting a note next to each of the key pairs — in a file or on a paper or anything else; it's up to you.

**Keep the keys safe. You may want to encrypt them and store securely.**

### 8. Contact the U°OS developers

Think up an account name that you would like to register as a Block Producer.

The account name has the following conventions:

* Must start with a letter or digit
* Must be 12 characters
* Can only contain the characters lowercase a-z and 1-5

For example, `123example345` meets the convention requirements.

Prepare the information that you will need to provide to the U°OS developers:

* Your preferred account name
* Your Owner public key
* Your Active public key

Contact the U°OS general group in Telegram at [https://t.me/uos_network_en](https://t.me/uos_network_en).

PM the group Admin for the U°OS Block Producers Telegram group.

Once you join the U°OS Block Producers Telegram group, provide your account name, owner and active public keys. The developers will register you as a Standby Block Producer.

### 9. Create and modify config.ini

1. Start the node once to create a default `config.ini` file:

    ```
    ~/opt/eosio/bin/nodeos --data-dir ~/uosdata/uos/data/ --config-dir ~/uosdata/uos/data
    ```

    The ```config.ini``` file will be created in the ```~/uosdata/uos/data/``` directory.

2. Open ```config.ini``` for editing and add the following lines:

    ```
    agent-name = "PRODUCER_NAME"
    producer-name = PRODUCER_NAME
    signature-provider = PUBLIC_KEY=KEY:PRIVATE_KEY
    p2p-peer-address = node-1.uos.network:9876
    p2p-peer-address = node-2.uos.network:9876
    p2p-peer-address = node-3.uos.network:9876
    p2p-peer-address = node-4.uos.network:9876
    p2p-peer-address = node-5.uos.network:9876
    ```

    where

    * PRODUCER_NAME — Your account name that you provided to the U°OS developers earlier
    * PUBLIC_KEY — Your public key from the Producer key pair that you generated earlier
    * PRIVATE_KEY — Your private key from the Producer key pair that you generated earlier

3. Save the file.

Note that the default `config.ini` file has the `agent-name = "EOS Test Agent"` parameter uncommented, so you will need to comment it (#) or replace with the `agent-name`, `producer-name` and `signature-provider` parameters as specified above. If you don't do this, you will get an error when starting your node.

### 10. Download genesis.json

Download the pre-created `genesis.json` file from the U°OS repository to your `~/uosdata/uos/data/` directory:

```
wget https://raw.githubusercontent.com/UOSnetwork/uos.docs/master/testnetv1/genesis.json
```

### 11. Start your node

Start your Standby Block Producer node:

```
~/opt/eosio/bin/nodeos --data-dir ~/uosdata/uos/data/ --genesis-json ~/uosdata/uos/data/genesis.json --config-dir ~/uosdata/uos/data "$@" > ~/uosdata/uos/data/stdout.txt 2> ~/uosdata/uos/data/stderr.txt &
```

Check that the node is running:

```
tail -f ~/uosdata/uos/data/stderr.txt
```

This should give you a running list of blocks and Block Producers.

### 12. Create a wallet and import Active and Block Producer private keys

Create a wallet that you will use to stake UOS and receive UOS emission:

```
cleos wallet create -n NAME --to-console
```

where

* `NAME` — Any name for your wallet
* `--to-console` — The wallet password will be printed to console. You can also specify --file instead of --to-console if you would like the password to be saved to a file instead.

Save the wallet password and keep it secure.

Make sure the wallet is unlocked:

```
cleos wallet list
```

This will print all your wallet names. The unlocked wallets will have an asterisk next to the name `*`.

For example, the wallet ledgerblocks is unlocked in this output:

Wallets:

```
[
"default",
"ledgerblocks *",
"test"
]
```

If your wallet is locked, you can unlock it with the following command:

```
cleos wallet unlock -n NAME
```

where `NAME` is the name of your wallet.

Import your Active private key into the unlocked wallet:

```
cleos wallet import -n NAME --private-key PRIVATE_KEY
```

Import your Block Producer private key with the same command but with your Block Producer private key this time.

Lock your wallet:

```
cleos wallet lock -n NAME
```

Now you have a locked wallet with both your Active and Block Producer private keys.

### 13. Register as a Block Producer

Run the following command:

```
cleos -u https://api-node-1.u.community:7888 system regproducer NAME PUBLIC_KEY
```

where

* `-u` — This parameter sends the command to a full U°OS node. Registration will only work on a fully synced node and syncing the node takes a significant amount of time. So use the -u parameter to register on a fully synced U°OS node running on U°Community server.
* `NAME` — This is your Block Producer account name.
* `PUBLIC_KEY` — This is your Block Producer public key.

For example, we are registering as `ledgerblocks` for this guide:

```
cleos -u https://api-node-1.u.community:7888 system regproducer ledgerblocks EOS8Apwg8bfaLWat4qizAdyoLgESCmkfA3Fz7gVnzzn9TfXaoH2iK
```

The command might print a warning:

```
warning: transaction executed locally, but may not be confirmed by the network yet
```

This is a standard warning saying that it may take a second to register on the network.

You can now check your account name on the [GOVERNANCE page of U°Community](https://u.community/governance).

## Troubleshooting and maintenance <a name="troubleshoot"></a>

Checking your registered Block Producer account on the GOVERNANCE page of U°Community:

* [https://u.community/governance](https://u.community/governance)

Checking if the node is running:

```
ps -elf | grep nodeos
```

Checking the produced blocks:

```
tail -f ~/uosdata/uos/data/stderr.txt
```

Gracefully stopping the node:

```
pkill nodeos
```

Deleting all blocks to restart the node fresh:

```
~/opt/eosio/bin/nodeos --data-dir ~/uosdata/uos/data/ --delete-all-blocks --config-dir ~/uosdata/uos/data "$@" > ~/uosdata/uos/data/stdout.txt 2> ~/uosdata/uos/data/stderr.txt &
```

You might want to do this if you started your node prematurely without properly following the instructions.

A full running U°OS node for API calls:

```
https://api-node-1.u.community:7888
```

Get any account information, including balances and voting:

```
cleos -u https://api-node-1.u.community:7888 get account NAME
```

Feel free to talk to the developers in the chat.

See also [CONTRIBUTING](../../../uos.docs/blob/master/CONTRIBUTING.md) for detailed project information.
