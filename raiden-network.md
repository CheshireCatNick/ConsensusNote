Raiden Network
==
## Idea
1. Only use blockchain when necessary (open and close a channel).
2. Only publish the final transfer result to blockchain.
3. Solving scalability, latency, privacy and high transaction fee issues in blockchain

## Raiden Network v.s. Lightning Network
- The key idea of these two networks are almost the same. What makes LN so infamous and RN so promising?
- RN is able to exchange tokens, interact with smart contracts and DEX(?), while LN is limited to BTC.
- [Reference](https://steemit.com/bitcoin/@mooncryption/scaling-cryptos-bitcoin-lightning-network-vs-ethereum-raiden-network)

## uRaiden
1. Already off-the-shelf and currently under some security test
2. Implement a many-to-one transfer model

## Problems for LN and RN
1. Routing is difficult.
2. Token is locked (in a smart contract) when channel is still open.
3. Large transfer is difficult to find a route. But people can just do it on-chain.
4. Centralized hub. Is it bad?
5. 

## Problems for Our Application
1. It is fast and cheap only if you transfer many times. If you've already opened a channel, then this is not an issue. Otherwise, opening a channel still costs transaction fee and blockchain time.
2. Protocol level fee and peripheral fee (paid by RDN).
3. There's no release date announced.
4. How to prevent a bot?
5. How to achieve fairness? This can be achieved if we have enough nodes.
6. How to know the A's token is actually from our wallet?
7. How about releasing our own token?
8. How to reward router with our token?

## Reasonable Design
1. It seems that if you want to use RN, you have to have at least one channel, or use som e "channel company" service.
1. We can't let our users open the channel. It is too slow and relatively expensive. If we use some channel company service, are there enough nodes to achieve fairness?
2. 

## Problems I Don't Understand
1. What is protocol level fee?
2. Why are there only two participants in a channel? Can't there be more participants? A: Double-spent issue.
3. What if a channel on route closed? Does it matter? A: It can not be closed if you promise to participate in routing.

## Reference
- [Official Concept and FAQ](https://raiden.network/faq.html)
- [Official Explain](https://raiden.network/101.html)
- [Centralize Proof](https://medium.com/@jonaldfyookball/mathematical-proof-that-the-lightning-network-cannot-be-a-decentralized-bitcoin-scaling-solution-1b8147650800)