
# Setup Environment

This example will use python3 ([web3](https://web3py.readthedocs.io/en/latest/quickstart.html)) and [greenfield cmd tool](https://github.com/bnb-chain/greenfield-cmd). We will use greenfield [TestNet](https://docs.bnbchain.org/docs/beaconchain/develop/rpc#testnet) environment in this example. 

## Clone greenfield-nft-migration Repo
```
git clone git@github.com:bnb-chain/greenfield-nft-migration.git
```

## Setup python virtual envs
```
# Install virtualenv if it is not available:
$ sudo pip install virtualenv
# Create a virtual environment:
$ virtualenv -p python3 ~/.venv-nft
# Activate your new virtual environment:
$ source ~/.venv-nft/bin/activate
```
## Install Python3 and web3 module
```shell
pip install --upgrade pip setuptools
pip install -r requirements.txt
```


# Setup Greenfield CMD tool
You can refer to https://docs.bnbchain.org/greenfield-docs/docs/tutorials/cli/file-management/overview

## download binary file
Download latest release of greenfield-cmd for either linux or mac. E.g.
```
cd greenfield-nft-migration/nft-migrate/
wget https://github.com/bnb-chain/greenfield-cmd/releases/download/v1.0.2/gnfd-cmd_mac -O ./gnfd-cmd
chmod +x ./gnfd-cmd
```

## Config Network


Edit the config toml file at 
```
vim greenfield-nft-migration/nft-migrate/config.toml
```
And input the following testnet network and save:

```
rpcAddr = "https://gnfd-testnet-fullnode-tendermint-us.bnbchain.org:443"
chainId = "greenfield_5600-1"
```

## Impport Account and Generating Keystore

Reference: https://docs.bnbchain.org/greenfield-docs/docs/tutorials/cli/file-management/overview#impport-account-and-generating-keystore


```
./gnfd-cmd account import key.txt

```

Create a password.txt file and input your password you use to import your account in last step. 
```
vim password.txt
```

### Migrate NTFs

Run the nft migration python script:

Get your NFT contact , we take 0xA5FDb0822bf82De3315f1766574547115E99016f as an example. It's an ERC721 contract deployed on BSC Testnet. 

Run
```
python3 migrate-nft.py --contract=0xA5FDb0822bf82De3315f1766574547115E99016f

```


