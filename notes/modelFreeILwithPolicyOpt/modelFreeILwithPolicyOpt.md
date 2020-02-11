# Discriminator Actor Critic: Addressing Sample Inefficiency and Reward Bias in Aversarial Imitation Learning (DAC)
#### Krostrikov et al. (2018)

In this work, the authors adapt REINFORCE and TRPO to the task of Imitation Learning in the Apprenticeship Learning framework.

**Note**: This paper provides a very nice overview of the TRPO algorithm and the Apprenticeship Learning formalism.

### Apprenticeship Learning

Apprenticeship Learning aims at learning a policy \pi that performs as well as the expert on an unknown true cost function. To do this, an AL algorithm will assume that that true cost function belongs to some class of function (e.g. linear combination of known cost functions) and then will aim to learn a policy so that its cost is smaller or equal to the expert's cost on all possible cost functions of this family.

To instantiate this framework, two ingredients must be provided:
  * a cost function class C
  * an optimisation algorithm to minize the difference between our policy's expected cost and the experts's expected cost

### Policy Optimisation for Apprenticeship Learning

The authors present two methods to approximately minimize the expected costs difference assuming access to a method for finding the particular cost function c \in C that maximise this difference given a fixed policy \pi. These two methods, IM-REINFORCE and IM-TRPO are adaptations to imitation learning of the respective RL algorithms.

They test their algorithms on a variety of tasks including gridworlds, Waterworld (Karpathy) and a Hughway Driving task (Levine).
