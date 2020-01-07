# How to run node for UOS

### Install docker and create user
```
adduser eos
apt-get update
apt-get install apt-transport-https ca-certificates curl gnupg-agent  software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io
usermod -aG docker eos
su - eos
```
### Create dirs and download snapshot and blocks.log
```
mkdir -p ~/.local/share/eosio/nodeos/data/snapshots
mkdir -p ~/.local/share/eosio/nodeos/data/blocks

docker run -d --log-opt max-size=100m --log-opt max-file=5 --name uos-node -v /home/eos/.local/share/eosio:/root/.local/share/eosio -p 127.0.0.1:8888:8888 -p 9876:9876 uosproject/uos:1.8.7
docker stop uos-node
docker rm uos-node

wget -O ~/.local/share/eosio/nodeos/data/snapshots/snapshot_latest.bin https://s3.eu-central-1.amazonaws.com/snapshot.uos.network/snapshot_latest.bin
wget -O ~/.local/share/eosio/nodeos/data/blocks/blocks.log https://s3.eu-central-1.amazonaws.com/snapshot.uos.network/blocks.log

```
default config.ini created at `~/.local/share/eosio/nodeos/config/config.ini`
### Edit config.ini
```
nano ~/.local/share/eosio/nodeos/config/config.ini
p2p-peer-address = mainnet-node-1.uos.network:9876
p2p-peer-address = mainnet-node-2.uos.network:9876
p2p-peer-address = mainnet-node-3.uos.network:9876
p2p-peer-address = mainnet-node-4.uos.network:9876
p2p-peer-address = mainnet-node-5.uos.network:9876
```
### Start docker container
First, start docker container with `--snapshot` param:
```
docker run -d --log-opt max-size=100m --log-opt max-file=5 --name uos-node -v /home/eos/.local/share/eosio:/root/.local/share/eosio -p 127.0.0.1:8889:8888 -p 9876:9876 uosproject/uos:1.8.7 /root/eosio/1.8/bin/nodeos --snapshot /root/.local/share/eosio/nodeos/data/snapshots/snapshot-latest.bin
docker logs -f uos-node
```
Then, stop and remove docker container after syncing:
```
docker stop uos-node
docker rm uos-node
```
Then, restart docker container without any params:
```
docker run -d --log-opt max-size=100m --log-opt max-file=5 --name uos-node -v /home/eos/.local/share/eosio:/root/.local/share/eosio -p 127.0.0.1:8889:8888 -p 9876:9876 uosproject/uos:1.8.7
```
