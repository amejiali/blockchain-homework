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
    
  e. 
      
      




## Instructions

### Setup the custom out-of-the-box blockchain

* Create a new project directory for your new network. Call it whatever you want!

* Create a "Screenshots" folder inside of the project directory.

* Create accounts for two (or more) nodes for the network with a separate `datadir` for each using `geth`.

* Run `puppeth`, name your network, and select the option to configure a new genesis block.

* Choose the `Clique (Proof of Authority)` consensus algorithm.

* Paste both account addresses from the first step one at a time into the list of accounts to seal.

* Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.

* You can choose `no` for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.

* Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.

* Export genesis configurations. This will fail to create two of the files, but you only need `networkname.json`.

* You can delete the `networkname-harmony.json` file.

* Screenshot the `puppeth` configuration once complete and save it to the Screenshots folder.

* Initialize each node with the new `networkname.json` with `geth`.

* Run the first node, unlock the account, enable mining, and the RPC flag. Only one node needs RPC enabled.

* Set a different peer port for the second node and use the first node's `enode` address as the `bootnode` flag.

* Be sure to unlock the account and enable mining on the second node!

* You should now see both nodes producing new blocks, congratulations!

### Send a test transaction

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
