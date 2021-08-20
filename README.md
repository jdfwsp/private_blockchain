# Building a Private Blockchain

## Tools needed
* [Geth](https://geth.ethereum.org/docs/install-and-build/installing-geth) - 1 of 3 original implementations of the Ethereum protocol written in Go (C++ and Python are the other 2)
* [MyCrypto](https://download.mycrypto.com/) - Desktop application for maintaining Ethereum accounts

## Create nodes
* Use Geth CLI tool to create 2 nodes that will run on your blockchain network
```
geth --datadir node1 account new
geth --datadir node2 account new
```

## Create network and genesis block
* Launch the network manager tool installed that comes with Geth
```
puppeth
```
* Follow the prompts to your specifications

**Chain ID** - Unique identifier of your blockchain used by MyCrypto app to connect and manage

**Blocktime** - Amount of time to mine one block

**Sealing accounts** - Account addresses of your nodes that can seal new blocks

**Prefunded accounts** - Account addresses of the nodes you want to populate with *fake cryptocurrency*

## Initialize nodes on new network
* Assign nodes to newly-created blockchain
```
geth --datadir node1 init network.json
geth --datadir node2 init network.json
```
* Connect nodes to blockchain
```
geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock
geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
```
* Commonly used flags:

    --datadir - Data directory for the databases and keystore

    --unlock - Comma separated list of accounts to unlock

    --mine - Enable mining

    --rpc - Enable the HTTP-RPC server (deprecated and will be removed June 2021, use --http)

    --allow-insecure-unlock - Allow insecure account unlocking when account-related RPCs are exposed by http

    --port - Network listening port (default: 30303)

    --bootnodes - Comma separated enode URLs for P2P discovery bootstrap
    
    --ipcdisable - Disable the IPC-RPC server

## Connect MyCrypto to new network


## Send transaction from one node to the other