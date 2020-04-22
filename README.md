# Proof of Authority Development Chain


## Instructions

The following steps were persormed to create the network (amnetwork) and the nodes (node1 and node2):

1. inside the directory AM_Network:

  a. Create the node1:
  
      geth account new --datadir node1
      Pswd: node1pswd
      Public Address: 0x1B65f58873803e8d12E2E1bF2989FDAd071Af799
      Path of the secret key file: node1/keystore/UTC--2020-04-21T04-08-42.804293000Z-1b65f58873803e8d12e2e1bf2989fdad071af799
      
  b. Create the node2:
  
      geth account new --datadir node2
      Pswd: node2pswd
      Public Address: 0x733Fa57D0853f3839525C0A5000627cB2FB7c782
      Path of the secret key file: node2/keystore/UTC--2020-04-21T04-09-27.759705000Z-733fa57d0853f3839525c0a5000627cb2fb7c782

  c. Create the network amnetwork:
  
      puppet
      with the following setup:
      
 ![amnetwork](AM_Network/Screenshots/puppeth_config.png)
  
  
  d. Init the nodes:
      
      once created, In a separate Terminal Window, in the AM_Network directory, run the init comads for the nodes:
      
      geth init amnetwork.json --datadir node1
      geth init amnetwork.json --datadir node2
    
  e. Run the first node, unlock the account (password node1pswd), enable mining:
  
      geth --datadir node1 --mine --minerthreads 1 --unlock 0x1B65f58873803e8d12E2E1bF2989FDAd071Af799
      
  f. In a differtent Terminal Window, run the second node with --rpc (HTTP access) enable, a different peer port (30304), and use the first node's `enode` address as the `bootnode` flag:
  
      geth --datadir node2 --port 30304 --rpc --mine --minerthreads 1 --bootnodes " enode://f3e21fd5b447903ac0148f25273c66acf3fb93c72012df1b6bcbaedce0214afeaca51b7510a365bcdaed6c055f83929c4af83933014f7bd74a6bcd44e82a5a47@127.0.0.1:30303"
      
      
2. Send a test transaction:





* Use the MyCrypto GUI wallet to connect to the node with the exposed RPC port.

* You will need to use a custom network, and include the chain ID, and use ETH as the currency.

![custom-node](Images/custom-node.png)

* Import the keystore file from the `node1/keystore` directory into MyCrypto. This will import the private key.

* Send a transaction from the `node1` account to the `node2` account.

* Copy the transaction hash and paste it into the "TX Status" section of the app, or click "TX Status" in the popup.

* Screenshot the transaction metadata (status, tx hash, block number, etc) and save it to your Screenshots folder.

* Celebrate, you just created a blockchain and sent a transaction!

![transaction-success](Images/transaction-success.png)

### Create a repository, and instructions for launching the chain

* Create a `README.md` in your project directory and create documentation that explains how to start the network.

* Remember to include any environment setup instructions and dependencies.

* Be sure to include all of the `geth` flags required to get both nodes to mine and explain what they mean.

* Explain the configuration of the network, such as it's blocktime, chain ID, account passwords, ports, etc.

* Explain how to connect MyCrypto to your network and demonstrate (via screenshots and steps) and send a transaction.

* Upload the code, including the `networkname.json` and node folders.

### Remember, *never* share your mainnet private keys! This is a testnet, so coins have no value here!

### Challenge mode

* Create a separate `bootnode` dedicated to connecting peers together

* There will be a new DevOps engineer joining the team, add an additional sealer address to the network on the fly!
