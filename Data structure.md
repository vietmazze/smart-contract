
# **Data Structure**

## Linked List: 
linear collection of data elements, it is a data structure of a collection of nodes* which together represent a sequence. A node is a
basic unit used in comp science. It's a data point of a large data structure. Node in a linked list must be read in order from the begining as list are inherently sequential access. 
      
- list elements can be easily inserted or remove without reallocation or reorganization of the entire structure. Yet linked lists by themselves do not allow "random access"

## Binary search tree: 
a binary tree in which for each node, a value of all the nodes in left subtree is lesser or equal and value of all the nodes in the right subtree is greater.When searching in a binary tree, we look at the root and compare the search value. We know in binary tree, the lesser of the root will be on the left and so on.Binary tree allows us to discard subtrees and so on since we start at the root and work our way down, nothing the left has values less of the root and right always has value greater than root. This help binary tree to be fast lookup, addition and removal of items. 
              
## Hash Table: 
a structure that can map keys to value by using a hash function. Example: Putting a name into a hash through a hash function.             

## Directed Acylic Graph (DAG): 
A finite “directed graph” with no “directed cycles”. Directed graph is a graph that is a set of vertices connected by edges, where edges have a direction associated with them. But DAG is directed graph without a consistent directed sequence since it has no directed cycles. Acylic is non circular, it’s moving node to node by following the edges.

# **Cryptography**

## Public/Private Key Cryptography:
Refers to the cryptographic system that uses pairs of keys: public and private keys which are known only to the owner. 
This system allows for authentication and encryption.

## RSA(Rivest-Shamir-Adleman)
Is one of the first public-key cryptosysttems. A system base on the difficulty of the factorization of the product of two large prime numbers.   RSA rest on the difficulty of factorizing the product of two large prime numbers. You can multiple the two large prime number, but it will take you long time to find those two prime # from their multiplied. 
Cryptographic hash function: a one way function, that is impossible to invert. Only way is brute force search of possible match. 

## Merkle tree: 
A hash data structure tree where each leaf node is labelled with the hash of a data block and every non leaf node is labelled with cryptographic hash( or the hash of its previous hashes) . Merkle tree is use to verify the consistency and content of data. Merkle tree enable a user to verify whether or not a transaction is included in a block.
Merkle proofs: The Merkle root represents all the hashes in the tree, where if one hash is modified the entire tree is invalid. 


# Distributed System

## Consistency Systems:
Where there exist consistent rules for a model in which the devs follow in order for memory of the coding to happen naturally and predictable. 

## Concensus: 
In computer science, when you have a system whose components are located on diff networked computers, you run into the system reliability from one network to the other. Especially in a multi-agent systems. A concensus is the idea of requiring  number of agents to agree on in order to push/ commit a transaction to database. Concensus must be fault tolerant( even in cases of failure in some components, the system must continue to operate properly) and somehow put forth their candidate values and agree on a single consensus. 

## Linearization: 
In terms of transaction, a linearization order has a sequential ordering requirement that if T1 ends before T2 starts, then T1 must be ordered before T2. 

## Fault tolerant:
The property of a system that enables a system to continue operating properly in the even of the failure some of its components. 

## Paxos: 
A family of protocols for solving consensus in a network. It include spectrum of trade-offs between the number of processors, number of message delays, and activity levels. 

## Raft: 
Another protocols for consensus algorithm alternative to Paxos, with proven safe and additional feature. 

## Idea of liveness v.s Safety

## Byzantine Fault Tolerance:
A problem in which no two computers on a dectralized network can entirely guarantee that they are displaying the same data. Base on the story of Byzantine Generals, in which to plan an attack between 7 generals, they must communicate in message. It is important that every agrees to synchronize attack or retreat. The key errors are what if the messenger get captured and the message would not be delivered? What if one of the general is a traitor and sabotage by sending wrong messages to different general? Byzantine problem focus on this situation, nodes attempting to agree on the info and display it across the network. One of the achievement in this is through POW, another is POS. 
How does POW/ POS solve the problem? Or increase the probabilistic chance of achieving the solution? 
POW is time/energy consuming.. difficult for individual to alter a block as quick as transactions go through? 

## Idea of liveness v.s Safety

A database in which storage devices are not all attached to a common processor, but stored in multiple computers.

## Sharding
A type of database partitioning (horizontal) that separates very large databases into smaller, faster more easily managed parts 

# Intro to BTC

## Blockchain: 
A blockchain is a ledger(notebook) of facts, assign accross multiple computers around the world in a peer to peer network. Facts can be transactions, some type of data. In the blockchain, each member is anonymous and called nodes. Comunication inside a blockchain goes through a crytographic hash function that securely identify the sender and receiver. When a new transactions accur, a concensus is needed in order for the fact to appear on the ledger. The concensus is carry through a system of POW, where each block has the info and the next block follow the previous block to carry out the function through a random mathematical challenge.
 - peer-to-peer networks, public-key cryptography, and distributed consensus based on the resolution of a random mathematical challenge.
 - ### A blockchain uses: 
 - the block timestamp (e.g. 1637-09-15 20:52:38) and
 - the hash from the previous block (e.g. edbd4e11e69bc399a9ccd8faaea44fb27410fe8e3023bb9462450a0a9c4caa1b) and finally
 - the block data (e.g. Transaction Data...)
 - to calculate the new hash digest checksum, that is, the hash e.g. 
 
## Replay Attack:
When you have two ledgers that share the same history and txs, such as the hard fork of BCH, both ledgers will share the same history and the amount hold. What if you want to send some transaction on only 1 ledger? it turns out, a person can copy the same transaction that you have done on one ledger to the other... since your transaction is valid on both ledgers. The person who presents the copy of the check on the other ledger is replaying the transaction. This is a problem since you wanted to send on only one ledger. We call this a replay attack. 
 - Bitcoin Cash solved this problem by changing the check ever so slightly. They created a special mark on the check that identified the check was for the BCH ledger and not the other ledger.Thus, any node now auditing Bitcoin will automatically reject a Bitcoin Cash check since the check has that special mark. Anyone auditing Bitcoin Cash will reject a Bitcoin check since the check is missing the special mark. This special mark is called replay protection since it prevents replay attacks.
 - Current problem involves the SEGWIT2x hard fork refusing to add a replay protection
 
## Segregated Witness:
One of the problem in Bitcoin transaction is the Malleability, which describes the transaction hash(digital signatures) can be alter. Imagine having a bank check and someone alter the signature. What would be the problem? 
 -  Many people consider this a flaw because a user can potentially change a transaction ID. This could lead to extra bitcoin being sent if a user claims they never received the bitcoin and the sender checks the original transaction ID to verify (which would not exist on the block chain if the ID was changed).
 - With SegWit, the transaction identifier no longer takes into account the signature. This means that even if the attacker changes the signature, the transaction identifier stays the same.
