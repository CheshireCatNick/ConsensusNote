Raiblock
==
## Design Principle
1. feeless
2. fast, async
3. scalable
4. only keep track of the latest block

## System
### Blockchain and Consensus
1. Each account has its own blockchain.
2. Blockchains of all accounts and transactions form a block-lattice structure.
3. An easy PoW is performed when creating a block. This PoW is only for anti-spam instead of for consensus in Bitcoin. 
4. PoW can be precomputed before a transaction happens.
5. If there's a fork in blockchain, balanced-weight PoS is performed to vote and decide the valid block.
6. PoS can be done by representatives.
### Transaction
1. All funds are originated from the `genesis account` with `genesis balance`.
2. Fund transferring requires two transactions, send and receive block.
3. Transaction type: open, send, receive and change.

## Security Issues and Precautions
|Attack|Type|Description|Precaution|
|-|-|-|-|
|Block Gap Synchronization|DDoS|Request for block resync causing DDoS amplify attack.|Wait until a certain threshold of votes is received and start resync, otherwise consider it as junk data.|
|Transaction Flooding|DDoS|Send many unnecessary but valid transactions.|PoW|
|Sybil Attack|Consensus|Try to break consensus with many different entities(nodes).|Balance-weighted PoS|
|Penny-spend attack|DDoS|Spend infinitesimal transactions to drain memory of a node.|History pruning by access frequency.|
|Precomputed PoW attack|DDoS|Advanced version of Transaction Flooding|Investigating...|
|50% attack|Consensus|Lower the voting balance by DDoS, increasing "offline" funds.|Lack of incentive. Marketcap. Representative increases "online" funds. Reject transactions from forked account. Block cemening(Not developed yet).|
|Bootstrap Poisoning|Consensus|Bootstrapping into an old representative network where attacker has a lot of stake.|Pair with initial database of accounts and known-good block head.|

#### Seems like DDoS is the main issues when it comes to feeless system...

## Other Issues
1. If security property is based on marketcap, how to gain marketcap in the first place?
2. Async means they cannot build smart contract on it?
3. Is history pruning safe? What if all users only run "current" or "light" node? 
4. Representatives centralized?
5. PoS reward?