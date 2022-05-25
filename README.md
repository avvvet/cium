# Block Folder 

This module contains the logic for core block building for blockchain like adding the block and writing the transactions 


# blockchain_node

this module is meant for running the node for blockchian . it can on any port or ip address


# cmd 

This module contains the logic to get the localhost 

# utils 

This module is responsible for elliptic curve , signature , private key generating , public key generating , rest api call to blockchain node , the attributes that are coming from there.

# wallet 

structure for the wallet 


# wallet_app

This module contains the frontend and webapp part which will communicate with blockchain node.



TO RUN SINGLE NODE:-

/repo/                    cd blockchain_node 
/repo/blockchain_node/    go run . -port 5000

To check if node is running , go to 127.0.0.1:5000


The node at the start will have info about genesis block. 


TO RUN MULTIPLE NODES


Open a new terminal and repeat above steps with a different Port No.


/repo/                    cd blockchain_node 
/repo/blockchain_node/    go run . -port 5001

To check if node is running ,open browser and go to 127.0.0.1:5000   and  127.0.0.1:5001


CREATE WALLET :-

To create a wallet , navigate to wallet_app directory in the repository . Then run it on port 8080 and connect it to a running node which is at 127.0.0.1:5000 


cd wallet_app
go run . -port 8080 -gateway http://127.0.0.1:5000

To check if a new wallet is created , go to http://127.0.0.1:8080 .You will see a Public key , Private key and Blockchain Address 

Blockchain address is actually a user friendly and shorter version of Public Key

To test the functionality , open a new tab and open http://127.0.0.1:8080 . Now we have two wallets A and B . Send some tokens from wallet A to B using the Blockchain Address .
You will see the token transferred to wallet B . One of the nodes will validate the transaction and get the fees. The ongoing transactions can be seen at transaction pool



TRANSACTION POOL :-

Transaction pool is the place where contains all of unconfirmed transactions. Transaction pool is stored on a special device and its contents can be accessed, observed in real time.

To access the transaction pool of a particular node  , go to 127.0.0.1:5000/transactions

Change the port no. to access transactions pools of other nodes.











