# HW 18 - Blockchain

## Setup custom blockchain
1. Create accounts for 2 nodes
    * Use command `./geth account new --datadir node1zb1`
    * Use command `./geth account new --datadir node2zb2`
2. Run puppeth, name the network, select option to configure new genesis block
    * Run puppeth with `./puppeth`
    * Name it: `zbank`
    * Configure using Clique
    
    ![configuring](./Screenshots/configuring.png)
3. Paste addresses for accounts allowed to seal and to pre-fund
4. Set the network id to 333
![puppeth_config_json](./Screenshots/config_json.png)
5. Initialize each node to the network
    * Run `./geth init zbank.json --datadir node1zb1`
    * Run `./geth init zbank.json --datadir node2zb2`
6. Run 1st node, unlock account, enable mining, and enable RPC flag
    * Run `./geth --datadir node1zb1 --mine --minerthreads 1 --rpc --unlock "0x4dee08f2fcb254400fd17e87ca392af870f2958b" --allow-insecure-unlock`
7. Do the same for the 2nd node but bootnode off the 1st
    * Run `./geth --datadir node2zb2 --mine --unlock "0xeb40fa325161d9df54c69f4962890a1a3e52a350" --allow-insecure-unlock --port 30304 --bootnodes "enode://2081601070805cec8047341e21ac2bb5b287bd2db3844c5505b7d1d196667113142d0b56c12a68e8c44d196a570d7db24cf8b6a40fa69b26e9fec5ed9fe8d467@127.0.0.1:30303" --ipcdisable`
8. See both nodes succesfully mining:
![mining](./Screenshots/nodes_mining.png)

## Send test transaction
1. Set up custom network in MyCrypto
    * Parameters: Port 8545, chain id 333, name it zbank on ETH
    * (Just for example on how I did it)
![custom network](./Screenshots/mycryptosetup.png)
2. Open the keystore file for node1 to view it and be able to send transaction
![node1](./Screenshots/exposed_node1.png)
3. Specify to send the transaction to the second node's address
![pre_transaction](./Screenshots/pre_transanction.png)
4. Display succesful transaction data
![transaction_data](./Screenshots/transaction_data.png)