# Exercise 5
 **Give an Atomic Commit Protocol that satisfies the converse of condition AC3. That is, if all processes vote Yes, then the decision must be commit. Why is it not a good idea?**
<br>  

[_Fast paxos for dummies_ used in my answer](./lamport-paxos/fastpaxosfordummies.pdf)


![Atomic commit rules](./img/ac1-5.png)

A converse statement to the current AC3 would be the following
> The commit decision can only be reached if _no_ processes voted No.

The issue with having this kind of Atomic Commit protocol is that in cases of a mass failure of participant nodes, it would be possible to come to a commit decision with a minority. This issue would further be aggregated by the failing nodes who then achieve a stable state and do a majority vote contradicting the previous one. 


# Excercise 6
**Consider 2PC with the cooperative termination protocol. Describe a scenario (a particular execution) involving site failures only, which causes operational processes to become blocked.**

Reading up on 2PC cooperative termination.
![2PC cooperative termination](./img/2pc_coopTerm.png)

Well if q is uncertain then blocking may arise.

<!-- [Search for keyword "site failure"](https://cs.uwaterloo.ca/~bernard/courses/cs454/8.FaultTolerance.pdf) -->
According to the [paper on distributed recovery](https://paperzz.com/doc/7015030/distributed-recovery) the danger of blocking may arise in situations where a process which is in an uncertain state recovers from failure. The recovering process p will try to reach out to other processes to find out what the decision was (commit/abort). However, if p is the first to recover it will not be able to reach a decision and will remain in a blocked state even though initially it is an operational process. 

Another case an exceution scenario where processes become blocked is described in the third sentence in the following list [![Cooperative Termination Protocol, page 228](./img/coop_termination.png)](https://paperzz.com/doc/7015030/distributed-recovery)
<!-- Demonstrated an image hyperlink-->
So if 3 is the case for every process _q_ with which process _p_ tries to communicate, then a blocking state will occur until some process _q_ is repaired which _p_ can communicate with where either statement 1 or 2 hold true. Statement 1 here being that _q_ has either decided commit or abort and sends that decision to _p_, and statement 2 being that _q_ has not voted, but it can unilaterally decide abort and sends that decision to _q_.

# Excercise 7
**Show that Paxos is not live**


To ensure safety, Paxos guarantees that only proposed values can be chosen and learned, and that no two learners can learn two different values.

Paxos is safe but not live, since a number of rounds can happen concurrently. A liveness property is about ensuring progress, while a safety property is about ensuring that inconsistencies do not occur.

Paxos can not guarantee liveness, since is it not a given that it will reach termination due to the possibility of multiple rounds running concurrently.

Lets take a case where proposer _p_ sends a **prepare()** message and the acceptor _a_ returns a **promise(round r)**. Naturally the proposer then sends an **accept()** message, but right before _a_ receives this message another concurrently running proposer _p´_ sends its **prepare()** with a higher round number which then forces the acceptor to ignore the accept message since it is from a previous round. In turn, the first proposer can then send its own **prepare()** message again with a higher round number that the one sent by _p´_, right before _p´_ manages to send its own value in the **accept()** message. This is a loop that can go on indefinitely. Although the system will never reach an inconsistent state, it will also not reach termination point showing that Paxos is not live. In other words:



# Excercise 8
**Show that in Paxos, if we remove the promise that the acceptor does not participate in previous rounds, Paxos is not safe any more.**

Take an instance where we 

<!-- 
Another instance, prepare(7), promise(7,-,-), accept(7,13). But then one proposer is slow, so learn(7,13) does not go through from all the acceptors. Then a new round starts so we go prepare(8), promise(8,-,-), accept(8,17) which then gets accepted and sent as learn(8,17). So we eventually reach a vote, where the learners discard the learn(7,13) votes since it was not a majority. If a new round 9 were to being proposed and start, taking the values from the max last round shows its importance, since taking 13 from round 7 is not accepted when you have nodes that return value 17 from round 8.
-->
# Excercise 9
**Show that Fast Paxos is not safe if we assume the same number of crash failures of Paxos.**


With 9 acceptors, f is 2. (N-f/3)
