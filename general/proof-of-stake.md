Proof of Stake
==
## GHOST: Greedy Heaviest Observed Subtree
- Waste: When block mining speed is fast, two miners might mine a block at the same time. The one with less acceptance will be discarded.
- Centralized： This will lead to a centralized system, since a large mining pool can have  more acceptance.
- To solve the waste problem, the longest chain (chain with the most PoW) is calculated including uncle blocks, which every block can declare.
- To solve the centralized problem, an uncle block can get reward (87.5%), while nephew gets 12.5%. Transaction fee is not award to uncle.
- Transactions in an uncle block is ignored.
- [ETH Ghost](https://github.com/ethereum/wiki/wiki/White-Paper#modified-ghost-implementation)
- [paper](https://eprint.iacr.org/2013/881.pdf)
- [uncle mining](https://bitslog.wordpress.com/2016/04/28/uncle-mining-an-ethereum-consensus-protocol-flaw/)

## Casper: a POS algorithm ETH used
- Block is now produced by validators, not miners.
- Every validator needs to lock an amount of ether as safe deposits (1000 ETH). If a validator violates rules of ETH network, his deposits will disappear. This addresses the "nothing at stake" problem.
- Validators are made to bet their deposits on how they expect everyone else to be betting their deposits.
- If you're bet is correct, you earn your deposits back with transaction fee. Otherwise you get less than your deposits. 
- PoW is also a betting scheme with electricity fee.
- Validators bet independently on blocks at every height (i.e. block number) by assigning it a probability and publishing it as a bet. A drastic change on probability bet will be punished.
- [reference](https://blog.ethereum.org/2015/08/01/introducing-casper-friendly-ghost/)