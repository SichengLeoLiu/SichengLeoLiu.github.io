# Reinforcement Learning (RL)
Supervised learning - need training samples

Reinforcement learning - agent interacts with environment with reward signals

The objective function of RL is as follow:
$$\pi^*=\underset{\pi}{\operatorname{\argmax}} E[\sum_{t \geq 0}\gamma^t r_t|S_0=s_0,\pi]$$
where $r_t$ denotes the reward at time step $t$, and $\pi$ is the strategy the agent to choose its actions. $\gamma\in(0,1)$ is used to determine whether the model focus on current reward or future reward. The smaller the $\gamma$ is, the model will more focus on current reward because the future reward is reduced by $\gamma$.

## Q-Value Function

Q-value function $Q$ determines the expected cumulative reward.
$$Q(s_0,a_0)=E[\sum_{t \geq 0}\gamma^t r_t|S_0=s_0,A_0=a_0,\pi]$$
and optimal Q-value ($Q^*$) can be achieved by the optimal policy $\pi^*$. The $Q^*$ should satisfies the following **Bellman equation** for iterative update:
$$Q^*=r+\gamma E_{s'\sim S}[\underset{a'}{\max}Q^*(s',a')|s,a]$$

### Store Q-Value

Steps to build a Q-table:
1. Initialize Q-table with all zero.
2. Choose an action.
3. Perform action.
4. Measure reward.
5. Update Q-table. (Back to step 2)

Q-Learning (update the state, off-policy) and Sarsa (also update the action, on-policy)

## Deep Q-Learning

It is infeasible to store all the Q-values in a table. Thus,  we use a neural network to store Q-values by approximating.