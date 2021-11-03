# Reinforcement Learning
<sub>27.okt</sub>

A learning object must be able to sense, take action and have a goal. Different from machine learning

In RL we focus on learning in a non-static environment. A reward is a scalar feedback signal. For example +ve rwear for forward motion, and -ve reward for falling over, when training a robot to walk.

One of the challenges in RL is the trade-off between exploration vs exploitation. Exploiting known information that leads to some reward is effective, but when should it find more information about the environment (explore), even though initially this may reape few rewards.
 Eat mac&cheese every day is OK, but if you explore and make new food, though you will have to go through some terrible dishes, at last you will find out about pasta which is way better than just mac&cheese.

Considering Observation, Reward, and Action: 
 $O_t + R_t -> A_t $


State determnis what happens next, and is defined as a function of the history: <br>$S_t = f(H_t)$ 


There is a distinction between environment state and agent state. Both env and agent have their internal reprsentaion, $S_a^t$  and $S_e^t$ ,respectively. 

In fully observable environments, agent state is the same as environment state. Our job is to build an agent state that is useful in predicting future events.

## The RL agent

The major components are:
- Policy: agents behaviour
  - A map from state to action
- Value function: how good is each state/action
  - Reward signal is immediate goodnes, value function is goodnes in the long run
  <!--  - $v\pi(s)=\sum\pi[R_t+1+\theta R_t+2..]$ -->
- Model
  - What follows what


### Problem
In which order should the reader query tags?
We want to query a device that has a new dat asample and avodi loss of data

As a RL problem, who would be the agent, Actions, rewards, state?