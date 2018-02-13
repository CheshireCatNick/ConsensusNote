Ouroboros
==
## Overview
1. first PoS with rigorous proof
2. PoS by electing slot leader
3. Generate randomness by MPC
4. Nash equilibrium design

## System Design
### Assumptions
- the network is synchronized with an upperbound
- a number of honest stakeholders is available to participate in each epoch
- the stakeholders do not remain offline for a long time
- adaptivity of corruption has small delay
- 51% of stake is in honest member. In that case, persistence and liveness can be proved.

### Ledger Properties
- persistence: after k confirmation, a node will either say a transaction x is stable, or not saying any other transaction stable that conflicts with x.
- liveness: transaction confirmation time in u slots

### Functionalities:
- diffuse: Be able to broadcast message to everyone.
- key and transaction: Be able to distribute public/private key and revoke a corrupted user. Adversary is consulted for corrupting users.

### PoS Election
- stakeholder: anyone who hold stake
- elector: any stakeholder who hold enough stake to be elected
- slot leader: a leader of a slot who can mint a block. A slot only has one leader, but a slot leader can be selected to lead multiple slots.
- slot: a short period of time
- epoch: several slot
- election: elector elect slot leader of the next epoch during this epoch
- forkable string: a string represent honest/malicious slot leader that can create a fork. Use this to proof the security of Ouroboros.

### Random Progress
- multiparty computation: to generate randomness, every elector needs to toss a coin and generate entropy
- commitment phase: elector generate a secret. Then, he encrypt the secret and split into shares. Then, he generate a commitment with encrypted share and proof of secret, signed it with private key and send it to others. Commitment is put into block.
- reveal phase: elector release his key and secret in opening message for others to verify. Opening is put into block. 
- recovery phase: in case some adversaries don't want to open their commitment, their commitment is recovered by honest elector's （publicly verifiable secret sharing）.
- follow the Satoshi: FTS will pick a coin randomly but verifiable. Elector who owns that coin becomes slot leader.

### Nash Equilibrium
- Input endorser: a set of stakeholders that endorse the input of a block. It's contribution will be acceptable after d slots late.
- Without endorsers' input, slot leader has to issue an empty block.
- 


## Challenges
1. Grinding attack: bias the random election
2. Nothing-at-stake: no punish for attacking. An attacker can try different kinds of histories alternatives at any point. Hash power can only be used once, while stake can be used several times.
3. Circularity: We need a consensus on random. If it is based on blockchain, this is a circularity.

## Security Issues
1. Double-spend is proved by persistence
2. Grinding attack: protected by coin tossing protocol which provides uniformly random result no matter what.
3. Transaction denial attack is proved by liveness.
4. Desynchronization attack: Party with more than 50% of stake must be synchronized.
5. Eclipse attack: Partition the network by manipulate p2p messages. Solution is the same as Desynchronous attack.
6. 51% attack: must own 51% stake.
7. Bribery attack: less possible than PoW, since the bribed shareholder has a lot of stake.
8. Long-range attack:
9. Nothing-at-stake attack: proved by forkable string. Even if an attacker brute-forces and fork, there will be none that is viable.
10. Past majority attack: a set of malicious shareholders from the past fork the blockchain. Only happens when:
    1. can only against stakeholders that are not frequently online
    2. stake shift is higher than some precondition
11. Selfish-mining: input endorser 



## Misc
- PoW and PoS is a randomized leader election proportion to CPU power/stake.
- [ELI5 Explain](https://cardanodocs.com/cardano/proof-of-stake/)
- Based on incentive structure and endorse transaction, they proved Ouroboros is approximate Nash equilibrium.
- Input endorsement?

