# FLP proof
<sub>28.okt </sub>

Consensus is not possible in an asynchronous system, and we are proving this.

Consensus only refers to correct nodes, where everybody gets to propose a value. If everyone agress on the same proposal, that is the decision. The value that is decided, is a proposed one. 
- Validity
- Agreement (correct node deides on a value) 
- Correctness (value must be a proposed one) 
- Termination (every participant eventually decides)

We want to break on those listed pillars above to prove that that consensus in async sys is impossible. 

## Model

An infinite number of messages in the message buffer, in a system with n processes and a message contains the sender, the data and the reciever.
message: (p,data, q) or $ \lambda $ where lambda is a null message which says that a system is async (i.e fishing out nulls instead of data)

An algoriithm $A$ is a sequence og steps. p can receive $\lambda$ even if there are messages for $p$ in the buffer. However if a process gets a message, eventually it __will__ get it. This is the liveness assumption. The one-time assumption is that p sends m to q at most once.

Binary consensus can prove general consensus. A configuration is a function that shows the state of the participants, as well as the quantity of set of messages in the buffer. A schedule is applicable to a configuration. If a step is applied to a configuration, you get a new configuration. Given a finite schedule and an inital state, you get a deterministically produced configuration.

A run of an algorithm A is a pair of an initial state I and a infinite schedule of A applicable to I.
> Every run of consensus is bound to produce infinte steps without a decision. Even with no crashes, it is the fact that there is the possibility of a crash that makes coordination and consensus impossible. Think of the two generals problem.

No matter what step you want to take it is always possible for the scheduler to insert some schedule such that the protocol goes froma bivalent state to a bivalent state, not allowing a monovalent state to be reached ( either 0 or 1 ), leading to unacceptable behaviour.

Lemma 1: THere exists a bivalent inital configuration.


Lemma 2: Let $S_1$ and $S_2$ be schedules applicable to some onfiguration $C$, and suppose that the processes takings steps in S_1 is disjoint from the set of processes taking steps in S_2.

Then; S_1;S_2 and S_2;S_1 are both sequences applicable to C, and they lead to the same configuration.


Lemma 3: Let C be bivalent, and let e be a step applicable to C. Then, there is a (possible empty) schedule S not containing e such that e(S(C)) is bivalent.


