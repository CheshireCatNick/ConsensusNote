Byteball
==
## Overview
- Generalized Bitcoin into a tamper proof storage which is not rewritable.
- Finality.
- No PoW.
- DAG, with transaction == block.
- User can define rules when issuing new asset (currency) in Byteball.
- Partial order, async.
- Many app is provided, such as transaction, messaging, voting, multi signing...

## Terms
- byte: Internal currency for payment to store data.
- main chain(MC): a chain from tip to genesis site constructed by selecting the best parent.
- witness: participants or company that has long established reputation or incentives to keep the network healthy.
- ball: finalized data
- Skiplist: hyperlink between balls, can be used to perform binary search.
- light clients: request proof chain (part of data interested) from full node.
- 


## System Design
- Includes as recent parent and as many parent as possible is incentivized.
- Circulation supply is 10^15.
- Transaction from the same account must include all of its previous units, directly or indirectly. All user follow this rule cannot double-spend.
- Total order is built by calculating main chain index.
- Best parent algo:
    1. stop traveling when we encountered majority of witness
    2. calculate witnessed level, the longest path length to genesis
    3. The parent with largest witness level is selected as the best parent
    4. Best parent cannot has more than one different witness.
- There's a point exists on MC and before it the MC will never change. Before that point we have finality.
- Non-serial unit is replaced by its hash.
- 
## Security
1. Double-spend: 
    1. with partial order: accept earlier one
    2. without partial order: construct total order later on and accept earlier one
2. Partition attack: At least on of the sides will lose majority of witnesses, which means they cannot advance their stable point.
3. User needs to select good witnesses and trust them.
4. 

## Other