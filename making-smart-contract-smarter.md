Making smart contract smarter
==

## Smart contract introduction
1. Example
2. Gas system

## Contribution
1. document several security vulnerabilities
2. formalize Ethereum semantics and provide a better one
3. provide Oyente, a symbolic execution tool
4. run Oyente on real Ethereum smart contract network and confirm some attacks

## Security issues
### weakness of smart contract
1. cannot be patched or upgraded
2. operates in an open network that arbitrary participants can join

### four possible attacks on smart contract
1. Transaction-ordering dependence
2. Timestamp dependence
3. Mishandled exceptions
4. Reentrancy vulnerability
    - the DAO hack
    - fork replay attack


## quick note
theDao attack
fork replay attack