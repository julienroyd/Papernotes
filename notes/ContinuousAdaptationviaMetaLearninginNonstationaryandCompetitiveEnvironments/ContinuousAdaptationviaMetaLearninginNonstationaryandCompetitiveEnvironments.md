# Continuous Adaptation via Meta-Learning in Nonstationary and Competitive Environments
#### Al-Shedivat, Abbeel *et al.* (2018)

In this work, the authors propose a gradient-based meta-learning approach to continuous earning in nonstationnary environments (like competitive multi-agent learning). The agent has to adapt continuously, both at training and execution time.

**Key Idea :** View nonstationnarity as a sequence of statinnary tasks, and train agents to *exploit dependancies* between consecutive tasks. Thus, they might be able to handle similar nonstationarities at execution time (test time).

**But,** seeing nonstationnarity from this perspective consequently places the agent in a few-shot regime (it only has a few steps/episodes to train on this pseudo-stationary environment before it changes again). This motivates the use of meta-learning, which is specializes in transferring knowledge from related tasks to perform better in a few-shot setting.

### Technical Approach

![#f03c15](https://placehold.it/15/f03c15/000000?text=+) `#f03c15` Hello

