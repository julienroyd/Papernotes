# Continuous Adaptation via Meta-Learning in Nonstationary and Competitive Environments
#### Al-Shedivat, Abbeel *et al.* (2018)

In this work, the authors propose a gradient-based meta-learning approach to continuous earning in nonstationary environments (e.g. competitive multi-agent learning). The agent has to adapt continuously, both at training and execution time.

**Key Idea :** View nonstationarity as a sequence of stationary tasks, and train agents to *exploit dependancies between consecutive tasks*. Like so, they might be able to handle similar nonstationarities at execution time (test time).

**But**, seeing nonstationnarity from this perspective consequently places the agent in a few-shot regime (it only has a few steps/episodes to train on this pseudo-stationary environment before it changes again). This motivates the use of meta-learning, which is specializes in transferring knowledge from related tasks to perform better in a few-shot setting.

### Technical Approach

![#f03c15](https://placehold.it/15/f03c15/000000?text=+) *This is the bulk of the paper.*

![#f03c15](https://placehold.it/15/f03c15/000000?text=+) *I will need to give this paper a second pass before being able to explain the relevant details of their mathematical approach*

### Other relevant details

##### Bias

Their method performs better than the other adaptation methods they compared with for trhe few-shot setting, but does not improve when going from the few-shot to regular training regime. They suggest that "the meta-learned strategy acquires a particular bias at training time that allows it to perform better from limited experience but also limits its capacity of utilizing more data". **(important limitation)**

##### On their training procedure to compare different algorithms

* **Pretained agents for static curriculum :** They pre-train agents by self-play, snapshot their policy as training goes on, and then train their true *agent-of-interest* against those pre-trained agent, but only for a few episodes per snapshot. This allows for a controlled training curriculum that end up creating *agents-of-interest* of balanced forces. Training these *agents-of-interest* independantly by self-play end up creating an unbalanced selection of agents (some are much stronger than others). **I think this is a good idea for comparing different algorithms particularities that have nothing to do with self-play schedule.**

* **Training pools** : At each iteration *k*, they :
  1. Randomly select an pre-trained opponent from the training pool
  2. Sample a version of the opponent's policy snapshot in [1, *k*]
  3. Rollout against that opponent (which is used to train the *agent-of-interest*)
