# Starting a U°OS Calculator Node

## Table of contents

* [Introduction](#introduction)
* [System requirements](#reqs)
* [Overview](#overview)
* [Step-by-step](#step)
* [Troubleshooting and maintenance](#troubleshoot)

## Introduction <a name="introduction"></a>

This document will guide you through starting a Calculator Node on the U°OS testnet.

As this is a testnet, here's a couple of things you need to know beforehand:

* The U°OS developers are currently registering Calculator Nodes manually. You will need to contact the U°OS developers on Telegram with your preferred account name and public keys.
* Your account name generated when signing up at [https://u.community/](https://u.community/) won't work for the U°OS Calculator Node registration. You will need to come up with a different one and provide it to us.

A Calculator Node calculates the Importance scores for every account on the U°OS blockchain.

The calculation is done continuously in 600 block cycles. The node follows the Block Producer voting pattern — the top 21 Calculator Nodes publish hashes of their calculation results to the U°OS blockchain.

UOS token emission is issued and distributed based on the Calculator Node results.

## System requirements <a name="reqs"></a>

Supported operating systems:

* Ubuntu
* Debian
* Fedora

RAM:

* 8 GB

Note that if you are running a Block Producer node, you will need a separate machine and a separate account to run the Calculator Node.

## Overview of the process <a name="overview"></a>

1. Install Boost C++ libraries
2. Time sync the system
3. Clone the U°OS repository
4. Update submodules
5. Build the U°OS software. Note that this will run for over an hour, so plan accordingly.
6. Install the node from the U°OS software
7. Generate two key pairs using the U°OS software
8. Contact the U°OS developers with your preferred account name and public keys
9. Create and modify `config.ini`
10. Download a pre-created `genesis.json` file
11. Start your node
12. Create a wallet and import both your Active and Owner private keys
13. Register as a Calculator Node


## Step-by-step <a name="step"></a>

### 1. Install the Boost C++ libraries

Install `libboost-all-dev`:

**Ubuntu/Debian**
```
apt -y install libboost-all-dev
```

**Fedora**
```
yum install boost-devel
```

### 2. Time sync the system

Sync the time to where your node is actually located. Check DigitalOcean: [How To Set Up Time Synchronization on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-time-synchronization-on-ubuntu-16-04).

For example, to sync to the Singapore time zone, run:

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

Update the submodules:

```
git submodule update --init --recursive
```

### 5. Build the U°OS software

Build the U°OS software with the following command:

```
./eosio_build.sh -s UOS
```

Note that this will run for over an hour, so plan accordingly.

### 6. Install the node

Install the node from the U°OS software:

```
sudo ./eosio_install.sh
```

Verify the version of the node:

```
nodeos --version
```

It will give you something similar to:

```
v.1.4.3
```

### 7. Generate two key pairs

You will need to generate two key pairs that you will use to manage your account:

* **Owner key pair**: Use this key pair to manage the ownership of your account; use the owner key to recover the active permissions if they get compromised.
* **Active key pair**: Use this key pair to transfer funds and vote.

Generate the key pairs:

```
cleos create key --to-console
```

The command will output a key pair once on each run. Run it two times to generate two key pairs.

Label each key pair as **Owner** and **Active**. Labeling here just means putting a note next to each of the key pairs — in a file or on a paper or anything else; it's up to you.

**Keep the keys safe. You may want to encrypt them and store securely.**

### 8. Contact the U°OS developers

Think up an account name that you would like to register as a Calculator Node.

The account name has the following conventions:

* Must start with a letter
* Must be 12 characters
* Can only contain the characters lowercase a-z and 1-5

For example, `123example345` meets the convention requirements.

Prepare the information that you will need to provide to the U°OS developers:

* Your preferred account name
* Your Owner public key
* Your Active public key

Contact the U°OS general group in Telegram at [https://t.me/uos_network_en](https://t.me/uos_network_en).

PM the group Admin for the U°OS Block Producers and Calculator Nodes Telegram group.

Once you join the Telegram group, provide your account name, owner and active public keys. The developers will register you as a Standby Block Calculator Node.

### 9. Create and modify config.ini

1. Start the node once to create a default `config.ini` file:

    ```
    nodeos --data-dir ~/uosdata/uos/data/ --config-dir ~/uosdata/uos/data
    ```

    The ```config.ini``` file will be created in the ```~/uosdata/uos/data/``` directory.

2. Open ```config.ini``` for editing and add the following lines:

    ```
    calculator-name = "CALCULATOR_NODE_NAME"
    calculator-public-key = "PUBLIC_KEY"
    calculator-private-key = "PRIVATE_KEY"
    plugin = eosio::chain_api_plugin
    plugin = eosio::history_api_plugin
    plugin = eosio::uos_rates
    p2p-peer-address = node-1.uos.network:9876
    p2p-peer-address = node-2.uos.network:9876
    p2p-peer-address = node-3.uos.network:9876
    p2p-peer-address = node-4.uos.network:9876
    p2p-peer-address = node-5.uos.network:9876
    ```

    where

    * CALCULATOR_NODE_NAME — Your account name that you provided to the U°OS developers earlier
    * PUBLIC_KEY — Your public key from the Active key pair that you generated earlier
    * PRIVATE_KEY — Your private key from the Active key pair that you generated earlier

3. Save the file.

Note that the default `config.ini` file has the `agent-name = "EOS Test Agent"` parameter uncommented, so you will need to comment it (#) or replace with the `calculator-name`, `calculator-public-key` and `calculator-private-key` parameters as specified above. If you don't do this, you will get an error when starting your node.

### 10. Download genesis.json

Download the pre-created `genesis.json` file from the U°OS repository to your `~/uosdata/uos/data/` directory:

```
wget https://raw.githubusercontent.com/UOSnetwork/uos.docs/master/testnetv1/genesis.json
```

### 11. Start your node

Start your Standby Calculator Node:

```
nodeos --data-dir ~/uosdata/uos/data/ --genesis-json ~/uosdata/uos/data/genesis.json --config-dir ~/uosdata/uos/data "$@" > ~/uosdata/uos/data/stdout.txt 2> ~/uosdata/uos/data/stderr.txt &
```

Check that the node is running:

```
tail -f ~/uosdata/uos/data/stderr.txt
```

This should give you a running list of blocks and Block Producers.

### 12. Create a wallet and import the Active private key

Create a wallet that you will use to stake UOS and receive UOS emission:

```
cleos wallet create -n NAME --to-console
```

where

* `NAME` — Any name for your wallet
* `--to-console` — The wallet password will be printed to console. You can also specify `--file` instead of `--to-console` if you would like the password to be saved to a file instead.

Save the wallet password and keep it secure.

Make sure the wallet is unlocked:

```
cleos wallet list
```

This will print all your wallet names. The unlocked wallets will have an asterisk next to the name `*`.

For example, the wallet `ledgerblocks` is unlocked in this output:

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

Lock your wallet:

```
cleos wallet lock -n NAME
```

Now you have a locked wallet with your Active private key.

### 13. Register as a Calculator Node

Run the following command:

```
cleos push action eosio regcalc '["NAME", "URL", LOCATION_CODE]' -p NAME
```

where

* `-p` — Permission level to authorize the action.
* `NAME` — This is your Calculator Node account name.
* `URL` — Additional information for your account identification in the Calculator Node list; usually your website or a U°Community link.
* `LOCATION_CODE` — Location code of the account

You should now be a Standby Calculator Node on the U°OS blockchain.

## Troubleshooting and maintenance <a name="troubleshoot"></a>

Checking if the node is running:

```
ps -elf | grep nodeos
```

Gracefully stopping the node:

```
pkill nodeos
```

Deleting all blocks to restart the node fresh:

```
nodeos --data-dir ~/uosdata/uos/data/ --delete-all-blocks --config-dir ~/uosdata/uos/data "$@" > ~/uosdata/uos/data/stdout.txt 2> ~/uosdata/uos/data/stderr.txt &
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

