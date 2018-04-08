Consensus Bound
==
### Comparison
|Consensus|Proof|Bound|
|-|-|-|
|IOTA|proof by probability, when attack = 1 total = 3, p(successfully attack) is low|2/3 online honest|
|XRB|N/A|51% online stake|
|Async|strictly proof by logic|1/2 honest if failed-stop, 2/3 honest if malicious, this is a bound|
|PBFT|based on Async|assume 2/3 honest to proof consensus algorithm is safe|
|Hashgraph|based on Async|assume 2/3 honest to proof consensus algorithm if safe|

### Proof
Simple proof: if 1 in 3 people is malicious, he can modify the message, or send two different messages to them, and the other two has no way to reach consensus.
General proof: if f in n nodes are faulty:
When we see f nodes die out, it is possible that there are all faulty nodes, or none of them are faulty nodes, we can't tell. Consider the second case, n - f > 2f => n > 3f

Another proof:
without time bound, we can only expect N - f messages, or the system may halt
received message (N - f) = honest(x) + malicious(f)
N - f = x + f
Since this protocol can only success if and only if x > f
or f can always 
x > f

N = x + 2f
N > 3f

### Core Concept
0. BFT:
    - a system can work with Byzantine fault / behavior (fail-stop or malicious node).

1. RB (Reliable Broadcast):
    - If sender of message is correct, all honest node must agree on the samge message. If sender is faulty, all honest node will either agree on the same message, or none of them agree on it.
    - Use 2pc. we not only need to know 2/3 of people know the message, but also know that 2/3 of people know 2/3 of people know the message.
    - PBFT: a system with leader can use RB to prevent fork.
    - Bitcoin does not need RB because one cannot easily find two blocks at a time.
    - Blockchain with some predefined rules doesn't need BA. Ex: longest chain or chain with min hash. We only need RBC.
    - Assume all honest node will have the same result with same input.

2. BA (consensus):
    - To reach consensus on a voting problem. Agreement means good nodes may not have the same belief, and they need agreement by voting (harder to decide). Many 3 rounds (1/3, 1/2, 2/3) converge to finalize. 
    - If there's just one dishonest node, it can make the whole system not converge. There's no deterministic solution if one process can crash. However, it can be solved if there is failure detector, partial synchrony or using randomization.
    - Byzantine Gerneral Problem
    - Every process pi propose a value vi. Eventually, all honest nodes must decide on a single value v, which is one of vi.
    - Total order broadcast problem <==> consensus problem

3. ACS: 
    - To agree on an array of element with size n
    - Need n times of BA

### Reference
[Byzantine Problem simple intro](https://yeasy.gitbooks.io/blockchain_guide/content/distribute_system/bft.html)
