#  Q-learning and the K-armed bandit problem
<sub>3.nov</sub>

K levers, and you can select only one.

Set of actions A. Evaluate the value of each action, i.e defining the action-value function. 

Action value: $ q_*(a)= \sum [R_t|A_t=a] $

Each action may have a reward with a different probability distribution. Say, Bernoulli, Binomial and Uniform.
q* is the mean of the dsitributions for each reward. The agent will have to run many test action to learn about the different reward distributions.

$ Q_t(A) = (\sum_(i=1)^(t-1)*R_i) \frac (t-1)$

The agent takes greedy action, meaning the actions are not chosen randomly but rather the action with the largest q value which translates to largest action reward.

The greedy function $a_T = argmax Q_t(a)$

The greedy function has the disadvantage of only exploiting previous knowledge, meaning actions which are seemingly inferior are never checked to see if they might yield better results over time.

**E-greedy** is an extension of the greedy function where it chooses randomly from time to time, and greedily the rest of the time.

To evaluate Q_n at time n we have the following formula: $Q_n + 1/2 [R_n-Q_n]$,

Having an optimistic intital value will mean that you are encouraging exploring more since the Q value of 1 will seem lower than say if the inital value is 0 and you pick action with Q 1, then it will be tempting to keep picking that one since it increases the Q.

### Summed
Methods to evaluate action values include: Sample average, or Incrementally (stationary- and nonstationary problems). <br>
Strategies for action selection include: _Random_, _greedy_, _e-greedy_ and _Optimistic initial values_


## Homework 1
Squad of n-drones, where some patroll and some are ferries
Each drone either keeps or sends the packet. Patrolling drones have the same trajectories (when coding, you don't know your trajectory, only you trajectory history). 

The monitoring drone moves seemingly randomly, and only comes back when it has a depleted battery. The ferry drone travels back and forth only from one point.