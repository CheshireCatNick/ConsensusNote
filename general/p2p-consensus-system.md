P2P Consensus System
==
## Intro
- Try to achieve general consensus in a p2p network
- Generalized Tangle
- Use ticket seller as an example
- Maybe PoS is needed to achieve fairness

## Attack we want to prevent
1. Early self-claimer: try to claim an earlier request time
2. Colluders: try to collude with others to get an earlier request time
3. Denier: try to make others time after his time
4. Garbage maker: make a lot of falsely requests, or randomly approve falsely requests

## Proposed system
1. A user wants to send a request for a ticket.
2. He first need to approve (prove) two other buyers.
3. After finishing the PoW, he can claim a time stamp (or counter) that is larger than any other site (allowed and not yet allowed) on the tangle. (this need to be reconsidered)
4. Server can start serving the site with smaller counter and high weight

## Attack resistance
1. Early self-claimer: If a user claims a counter that is smaller than previous users, other users will not allowed it
2. Colluders: One approve is not enough. we need to check the `weight` of a site. This is like "double spending"
3. Denier: not a problem. you can only approve or approve other tips. you can't deny a tip.
4. Garbage maker: design a tip select algorithm (hard)

## Open discussion
1. Can we solve general DDoS if we solve ticket selling problem?
    - In ticket selling system, we need to achieve fairness, while in general DDoS, we need to achieve availability.
    - We can no longer use real-name system to prevent garbage request maker.
    - Required time delay is smaller in general DDoS.
2. A tip select algorithm needs to be carefully designed to prevent garbage maker and achieve fairness.
3. After the weight is large enough, we believe the time when a user finish PoW. Is this fair? The weight-increased speed is not the same.
4. Can a full node select its own tips not according to Monte-carlo markov random chain?
5. How to verify a user's time is valid when everyone is seeing a "different" tangle?
6. 