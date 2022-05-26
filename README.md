
cium blockchain – a name drived from the Element Francium , dropping Francium, we get cium. 
It occurs naturally, it decays so quickly it's very rare. In fact, scientists have never had a large enough sample of francium to know what it actually looks like!

What do we have in this repo, 

- blockchain node
– a go application with integrated web server, ready to run in multiple instance in a given network address using unique ports

- to run it `cd to blockchain_node` and run `go run . Port 5000`.  to run multiple nodes use similar command with different `-port 500x`

- when the node run, it will generate automatically wallet address (blockchain address) that will be used to hold incentive token rewarded ,for participating in the network blockchain.

* For demonstration/development purpose , any participant node will be rewarded 1.0 CIUM per chain validation or new block creation.

* node consensus with nearby nodes would happen 20sec

* current mining difficultly is set to 3 leading zeros hashes

- each node will have its own temporary transaction pool before creating new block. Once mining happen and new block generated , transaction pool will be cleared by the node will be available for new transactions.

- each nodes with a given wallet address will response with total amount of the wallet

- the node comes to consensus taking the longest valid chains from the network.

- nodes use elliptic curve digital algorithm to generate asymmetric keys

- to view the temporary transaction pool of the node ``http://127.0.0.1:500x/transaction` 

- Wallet app

- autonomous web app node with web server that renders UI for user wallet interaction 
- generates non custodian wallet address (public and private key with short form of the public key)
- to the run the app `go run . -port 8080 -gateway http://127.0.0.1:5000`  the `- gateway flag is to   connect to nearest available blockchain node. (to do:  need to search nearby running node and attache)
- currently if the web app page loaded refreshed, new wallet address will be generated and attached.

Explorer – currently we can view blocks and transactions detail using any node address `http://127.0.0.1:500x/chain`

# Prime Lab Golang Blockchain Application

## block Folder 

This module contains the logic for core block building for blockchain like adding the block and writing the transactions 


## blockchain_node Folder

this module is meant for running the node for blockchian . it can on any port or ip address


## cmd Folder

This module contains the logic to get the localhost 

## utils Folder

This module is responsible for elliptic curve , signature , private key generating , public key generating , rest api call to blockchain node , the attributes that are coming from there.

## wallet Folder

structure for the wallet 


## wallet_app Folder

This module contains the frontend and webapp part which will communicate with blockchain node.

## What our Blockchain support?

#### Write a new Transaction to the blockchain.

#### Create a new multiple Wallet on your blockchain.

#### Reading
 1. View Transaction Status & Details
 2. View Overall Blockchain Status
 3. View Current Block
 4. Get Current Nodes List


# Working Diagram 
![image](https://user-images.githubusercontent.com/103436234/170375896-f5454d55-3bb3-4276-bfb1-3381198af184.png)


# How to run the Nodes, Wallets & Transactions?


## Nodes 
The node at the start will have info about genesis block. 

#### Follow the below steps to run nodes

1. Go to your code editor's terminal
2. Go to blockchain_node directory (... **cd blockchain_node** ... type in your terminal and press enter)
3. now run command in your terminal
   1. **go run . -port 5000**  
      1. **.** : run all go files inside of directory
   2. ... **go run blockchain_server.go main.go -port 5000** ...

1 node is running on port ***127.0.0.1:5000*** And for other 2 nodes you need to follow above steps  just change the port no. (Ex: node 1 is running at ***127.0.0.1:5000***, node 2 is running at ***127.0.0.1:5001*** and node 3 is running at ***127.0.0.1:5002***)


## WALLET :-

#### Follow the below steps to run wallet app

1. Go to your code editor's terminal
2. Go to wallet_app directory (... **cd wallet_app** ... type in your terminal and press enter)
3. now run command in your terminal
   1. **go run . -port 8080 -gateway http://127.0.0.1:5000** 
      1. **.** : run all go files inside of directory
   2. **go run main.go wallet_server.go -port 8080 -gateway http://127.0.0.1:5000** 
   3. You need running node as wallet app gateway

To check if a new wallet is created , go to http://127.0.0.1:8080 .You will see a Public key , Private key and Blockchain Address 

Blockchain address is actually a user friendly and shorter version of Public Key

To test the functionality , open a new tab and open http://127.0.0.1:8080 . Now we have two wallets A and B . Send some tokens from wallet A to B using the Blockchain Address .
You will see the token transferred to wallet B . One of the nodes will validate the transaction and get the fees. The ongoing transactions can be seen at transaction pool



## TRANSACTION POOL :-

Transaction pool is the place where contains all of unconfirmed transactions. Transaction pool is stored on a special device and its contents can be accessed, observed in real time.

To access the transaction pool of a particular node  , go to 127.0.0.1:5000/transactions

Change the port no. to access transactions pools of other nodes.











