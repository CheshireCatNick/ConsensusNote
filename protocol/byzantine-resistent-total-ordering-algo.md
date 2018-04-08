Byzantine-resistent Total Ordering Algorithms
==
## Principals
1. convert causal order into total order
2. fault model: crash and 'authenticated' Byzantine fault (with digital signature and digest)
3. network: asynchronous
4. Byzantine process does not send message to make other program crash.


## System (followed by non-faulty process)
### Basics
1. message m'' from process q follows message m from process p if:
    1. m'' acknowledge m
    2. m'' acknowledge m' where m' follows m
2. message m' from process q acknowledge m only if q received all messages m follows before broadcasting m'
3. message m' from q acknowledge all messages broacast earlier by q
4. Each process has internal state with two message set: total order set and causal order set
5. candidate message: a message only follows messages in total order set
6. Different non-faulty process may have different causal set, but they must decide on the same message to extend total order

### Properties
1. Reflexive
2. Transitive
3. A non-Byzantine process can not originate a message that occurs in cycle.
4. Basic 3
5. Any message from a non-Byzantine process does not acknowledge a message involved in a cycle.
6. liveness guerantee all non-faulty process generate messages that follow the message from non-faulty process.

### Causal Order
1. each message follows itself
2. if m follows m' and m' follows m'', m follows m''
3. if m follows m', m' does not follow m
4. if m and m' are from the same process, either m follows m' or m' follows m
5. if m follows m' and m' follows m (cycle), m'' from a non-byzantine process does not follow m or m'
6. if m is from a non-faulty process, every other non-faulty process exists a message m' follows m

### Voting
1. each candidate set has its own stages of voting
2. stage 0: a message vote for a candidate set that contains itself
3. stage i: a message vote for a candidate set that it follows "enough messages" that vote at stage i - 1
4. 


