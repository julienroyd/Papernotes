# Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with Stochastic Actor
#### Haarnoja, Zhou, Abbeel and Levine (2018)

In this work, the authors propose a new algorithm called Soft Actor Critic (SAC) which learns stochastic policies using off-policy data, the actor-critic parametrization and the maximum entropy framework. The main motivation is to alleviate two important limitations of model-free RL methods: very high sample complexity and brittle convergence properties (difficult hyperparameter tuning).

### Soft Policy Iteration (theoretical foundation)

Given the Maximum Entropy objective:

![maximum_entropy_framework](maximum_entropy_framework.png)

### Soft Actor Critic (practical algorithm using neural nets)
