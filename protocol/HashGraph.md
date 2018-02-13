HashGraph
==
## Design Principle
1. fair:
    1. no individual can manipulate the order of transactions
    2. no one can stop a transaction or delay it
2. fast
3. provable
4. Byzantine
5. ACID
6. efficient: no wasted block
7. inexpensive: no PoW
8. time stamp
9. DoS resistant
10. non-permissioned

## System
### Term Definition
1. see: w can see x if x is known to it and no forks by that creator are known to it. Ex: if forked blocks are x and y, w can see x if x is ancestor of w but y isn't.
2. strongly see: w can see more than 2n/3 events by different members that can see x. n is the number of members. It is proved that w can only strongly see one of the forked block.
3. famous witness: 2n/3 of witnesses in the next run can see it.
4. unique famous witness: a famous witness that does not have the same creator of any other famous witness created in the same round. If there's no fork, each famous witness is also unique famous witness. 
4. virtual voting: One vote for each witness event. decide whether a witness event is famous. For a witness x in r, each witnesses in r + 1 will vote it if it can see x. 
5. round (round created): if an event can strongly see 2n/3 witnesses in r, it is set to round r + 1
6. witness event: the first event in each round.
7. received round: x has received round r if that is the first round in which all the **unique famous witness event** were descendants of it, and the fame of every witness is decided less than or equal to r.
8. received time: if x received round = r and Alice create a unique famous witness y in r, and z be the earliest self-ancestor of y that learned x, and t is the time stamp Alice put in z, then t is the time when Alice first learned x. The received time is median of all time stamp.
9. coin round: assume there's an attacker that can control the message over the Internet, trying to keep the vote evenly split. A coin round is a round that anyone can vote randomly. This design will prevent such attack, since there's a chance that the community pass 2/3 * n threshold. Thus, we cliam that this system will reach consensus finally with probability 1.

### Algorithm
``` python
thread 1:
    choose a random member
    sync with him
thread 2:
    receive a sync
    create a new event
    # divide round by checking by checking if an event x can strongly see 2n/3 witnesses in r
    divideRounds()
    # decide if witness in r is famous by voting from witnesses in r + 1, collecting by witness in r + 2
    decideFame()
    # decide receive round of events. if an event x can be seen by all unique famous event in round r, its received round is r
    findOrder()
```
- Pseudo code of other procedures can be found in white paper
- Example can be found in Consensus.pdf

### Lemma
Many basic lemma and proof can be found in white paper
## Optimization and Enhancement
1. general PoS
2. signed state: for pruning old data
3. efficient gossip: sending only (eventCreator, eventParent, eventParentIndex) instead of two large hashes
4. fast election (algo)
5. fast calculation (algo)