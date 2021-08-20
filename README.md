# Building a Private Blockchain

## Tools needed
* [Geth](https://geth.ethereum.org/docs/install-and-build/installing-geth)
* [MyCrypto](https://download.mycrypto.com/)

## Create nodes
```
geth --datadir node1 account new
geth --datadir node2 account new
```

## Create network and genesis block
```
puppeth
```

## Initialize nodes on new network
```
geth --datadir node1 init network.json
geth --datadir node2 init network.json

geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock
geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
```

## Connect MyCrypto to new network


## Send transaction from one node to the other