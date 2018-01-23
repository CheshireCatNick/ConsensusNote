Consensus Bound
==
|Consensus|Proof|Bound|
|-|-|-|
|IOTA|proof by probability, when attack = 1 total = 3, p(successfully attack) is low|2/3 online honest|
|XRB|N/A|51% online stake|
|Async|strictly proof by logic|1/2 honest if failed-stop, 2/3 honest if malicious, this is a bound|
|PBFT|based on Async|assume 2/3 honest to proof consensus algorithm is safe|
|Hashgraph|based on Async|assume 2/3 honest to proof consensus algorithm if safe|