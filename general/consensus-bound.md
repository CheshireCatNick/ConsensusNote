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
Simple proof: if 1 in 3 people is malicious, he can modify the message, and the other two has no way to reach consensus.
General proof: if f in n nodes are faulty:
When we see f nodes die out, it is possible that there are all faulty nodes, or none of them are faulty nodes, we can't tell. Consider the second case, n - f > 2f => n > 3f

### Concept
1. To reach consensus, we not only need to know 2/3 of people know the message, but also know that 2/3 of people know 2/3 of people know the message.

### Byzantine Fault Tolerance v.s. Byzantine Agreement
- Fault tolerance means some nodes can be fail-stop or malicious, but good nodes will always vote the same. 3 rounds finalize.
- Agreement means good nodes may not have the same result, and they need agreement by voting (harder to decide). Many 3 rounds converge to finalize.

### Reference
[Byzantine Problem simple intro](https://yeasy.gitbooks.io/blockchain_guide/content/distribute_system/bft.html)
