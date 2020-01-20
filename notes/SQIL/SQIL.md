# SQIL: Imitation Learning via Reinforcement Learning with Sparse Rewards
#### Reddy et al. (2019)

In this work, the authors present a novel, surprisingly simple algorithm for Imitation Learning that performs on par or better than GAIL without requiring the use of an adversarial framework to learn a cost function.

### Algorithm

Key idea: Incentivize the agent agent to match the demonstrations over long time horizons by encouraging it to come back to demonstrated states when it has drifted to out-of-distribution states. This is simply implemented with three simple modifications to [Soft Q-Learning](https://dl.acm.org/doi/10.5555/3305381.3305521):

  * At initialisation, fill the experience replay buffer with expert trajectories (demonstrations) with rewards set to r=1
  * Adds new transitions encoutered by the agent to the replay buffer with reward r=0
  * When sampling from the replay buffer, balance 50-50 the number of demonstration v.s. encountered transitions

Check out the full algorithm and loss below:

![](SQIL_fig1.png)

![](SQIL_eq1.png)



### Theoretical contributions


### Experiments


