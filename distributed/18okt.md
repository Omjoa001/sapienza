## Consensus
18.okt

Paxos would have been live with a coordinator, but choosing a corodinator requires consensus so this is not possible.


No fault | Crash          |  Byzantine
------------ | -------------         |  ---
 1 round | f=1, f+1      | PBFT
 1 round | FLP, PAXOS, 2PC  | FLP, PBFT

To make consensus be safe and live in a synchronous system you need the byzantine nodes. If there are more than 1/3, it is not possible.