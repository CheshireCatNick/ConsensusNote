Consensus Bound
==
|Consensus|Proof|Bound|
|-|-|-|
|IOTA|proof by probability, when attack = 1 total = 3, p(successfully attack) is low|2/3 online honest|
|XRB|N/A|51% online stake|
|Async|strictly proof by logic|1/2 honest if failed-stop, 2/3 honest if malicious, this is a bound|
|PBFT|based on Async|assume 2/3 honest to proof consensus algorithm is safe|
|Hashgraph|based on Async|assume 2/3 honest to proof consensus algorithm if safe|

Simple proof: if 1 in 3 people is malicious, he can modify the message, and the other two has no way to reach consensus.
General proof: if f in n nodes are faulty:
When we see f nodes die out, it is possible that there are all faulty nodes, or none of them are faulty nodes, we can't tell. Consider the second case, n - f > 2f => n > 3f