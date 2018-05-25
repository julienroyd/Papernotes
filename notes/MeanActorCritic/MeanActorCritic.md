# Mean Actor Critic (MAC)
#### Asadi *et al.* (2018)

In this work the authors suggest a simple modification to the actor-critic framework: instead of computing the estimated gradient using only the actually sampled action, they compute the average over all possible actions.

**Note:** They apply this approach only to discrete control problems. A very similar approach offers a deeper theoretical analysis and extend the method to continuous control ([see Expected Policy Gradients (EPG)](https://arxiv.org/abs/1706.05374)) .

**Key aspects:**
* Uses the exact same architecture than Advatage Actor-Critic (A2C)
  * 1 two-headed network that produces on one side a distribution over actions (actor/policy) and real-valued outputs (critic/Q-function)
* Eliminates the need for a baseline to reduce variance (this can easily be mathematically proven)
* They prove that for a stochastic policy, MAC has stricktly lower variance than basic Actor-Critic

**Results:** Results on 2 classic-control problems (OpenAI) and 6 Atari-2600 games (DeepMind) are good, but not SOTA. However, they beat REINFORCE, Actor-Critic.

### Other Tricks
* They use an entropy term in the objective function to prevet premature convergence
